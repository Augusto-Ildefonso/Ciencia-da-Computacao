# Introdução
O fluxo de uma autenticação funciona da seguinte forma:
1. O usuário acessa uma página do front-end para fazer login e preenche com seu login e senha
2. O front-end envia uma requisição para o back-end com o login e senha do usuário
3. O back-end criptografa a senha fornecida pelo usuário junto com uma senha adicional que só o back-end conhece
4. O back-end se conecta com o banco de dados e verifica se existe algum usuário com aquele login e com aquela senha criptografada
5. O back-end gera um token jwt de acesso para o usuário (dentro do token existe a informação de id do usuário)
6. O back-end retorna o token para o front
7. O front pega o token do back-end e guarda na memória local (localStorage) para utilizá-lo nas próximas requisições

Quando o front-end quer acessar alguma rota que precisa estar logada no back-end:
1. O front-end passa pelo cabeçalho da requisição o token do usuário (o token pode ter data de validade)
2. O back-end verifica se é um token válido, pega o id do usuário do token e verifica no banco de dados se aquele usuário existe
3. O back-end processa o restante da requisição
# Requisitos
- MongoDB Database
- NodeJS
- ReactJS
# Dependências Necessárias
## Front-end
- axios
- react-router-dom
## Back-end
- bcryptjs
- body-parser
- cors
- esn
- express
- jsonwebtoken
- mongoose
# Back-end
## Conexão com Banco de dados
Primeiramente precisamos configurar a conexão com o banco de dados. Crie uma pasta dentro de source chamada database e dentro dela um arquivo chamado ``mongoose.js``. Copie o seguinte código dentro do arquivo, colocando na variável uri link que você copiou do monoDB.
```js
const mongoose = require('mongoose');

const uri = "CÓDIGO DO MONGO"

mongoose.connect(uri, {
	useNewUrlParser: true,
	useCreateIndex: true,
	useUnifiedTopology: true,
	useFindandModify: false,
});
```
## Modelo de Usuário
Agora, precisamos criar um Modelo de usuário para guardar os dados de nossos usuários. Dentro da pasta database, crie uma pasta chamada models e dentro dela um arquivo ``User.js``.

Vamos precisar dos seguintes imports:
~~~js
const mongoose = require('mongoose');
const bcrypt = requite('bcrypt');
const jwt = requite('jsonwebtoken');
~~~
Agora, vamos criar um modelo de usuário com login e password
~~~js
const userSchema = new mongoose.Schema({
	login:{
		type:string,
		required: true,
		trim: true,
	},
	password:{
		type: string,
		required: true,
		trim: true,
		minlength: 6,
	}
})
~~~
Agora, vamos criar um método que gera um token de acesso, utilizando o jsonwebtoken. Esse código pede uma chave de acesso que vamos chamar de "ICMCJR".
~~~js
userSchema.method.generateAuthToken = async function () {
	const user = this;
	const token = jwt.sign({_id: user._id.toString()}, 'ICMCJR');
	return token;
};
~~~
Agora, vamos criar um método para encontrar o usuário baseado em seu usuário e senha:
~~~js
userSchema.statics.findByCredentials = async (login, password) => {
	const user = await User.findOne({login});
	if(!user) return undefined;

	const isMatch = await bcrypt.compare(password, user.password);
	if(!isMatch) return undefined;

	return user;
};
~~~
Também devemos criar um método que executará antes de salvarmos o usuário, para criptografar a senha:
~~~js
userSchema.pre('save', async function (next){
	const user = this;

	if(user.isModified('password')){
		user.password = await bcrypt.hash(user.password, 8);
	}
	next();
});
~~~
Por fim, criamos efetivamente o modelo e o exportamos:
~~~js
const User = mongoose.model('User', userSchema);
module.exports = User;
~~~
## Controller de Usuário
Agora, vamos criar o controller para o nosso usuário, onde vão ficar os métodos de logar e de criar usuário. Também vamos criar um método teste, que só vai poder ser acessado quando o usuário fornecer um token válido.

Dentro de src, cria uma pasta chamada controllers e dentro dela um arquivo chamado ``UserController.js``. Dentro dese arquivo, primeiramente importamos o modelo de usuário e depois criamos nosso método de login:
~~~js
import User from '../database/models/User';

const login = async (req, res) => {
	try{
		let user = await User.findByCredentials(req.body.login, req.body.password);
		if(!user) return res.status(400).send({error: 'Wrong Credentials'});

		const token = await user.generateAuthToken();

		return res.status(200).send({token, login: user.login});
	} catch(error){
		console.log(error);
		return res.status(500).send({error});
	}
}
~~~
Esse método tenta encontrar o usuário através do login e password fornecido (utilizando o método que criamos anteriormente). Caso encontrada, geramos o token e enviamos o token e o login do usuário na volta da requisição.

Agora vamos criar um método para cadastrar um usuário e a rota de teste:
~~~js
const createUser = async (req, res) => {
	try{
		const user = new User({login: req.body.login, password: req.body.password});

		await user.save();
		const token = await user.generateAuthToken();

		return res.status(201).send({token, login: user.login});
	} catch (error){
		return res.status(400).send({error);
	}
};
 
	const testRoute = async (req, res) => {
		return res.status(200).send('Seja bem-vindo ${req.user.login}!');
	}
~~~
Para finalizar, vamos exportar os métodos:
~~~js
export default {login, createUser, testRoute};
~~~
