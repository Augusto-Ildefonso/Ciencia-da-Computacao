# O que é NodeJS
Ele é um interpretador de código javascript para servidores
# O que é NPM
NPM é o gerenciador de pacotes do Node. Ele é o responsável por instalar módulos e gerenciar dependências.
# Iniciando um projeto
Para iniciar um projeto, basta criar uma pasta, digitar `npm init` e responder as perguntas:
- package name: nomedoprojetoapi
- version: (deixar em branco)
- description: breve descrição do projeto
- entry point: src/index.js
- test command: (deixar em branco)
- git repository: link para gitlab/github
- keywords: (deixar em branco)
- author: autor
- license: (deixar em branco)

Com isso, será criado um arquivo package.json com as informações fornecidas acima. Nesse arquivo ficam os scripts (scripts essenciais para o projeto como start, test, etc...), dependências (todas as bibliotecas das quais seu projeto depende) e algumas configurações de dependências.
# Scritps
Para dar início ao projeto é necessário adicionar um script. Para iniciar um projeto no NodeJS, basta digitar:
```
$ node index.js
```
Portanto, incluiremos nos scripts do package.json um script contendo isso chamado start:
~~~json
"scritps":{
	"start": "node src/index.js"
},
~~~
Agora, pode-se executar `npm run start`. Sempre que for executar um script tem que colocar o `run`, exceto se o script for o start.
# Dependências
Para incluir dependências no projeto, basta digitar:
```
$ npm instal --save nome-da-dependencia
ou
$ npm i --save nome-da-dependencia
```
A flag `--save` indica que a dependência deve ser adicionada ao package.json. 
# Node Modules
Ao se instalar uma dependência, no seu repositório será criado:
- Uma pasta: "node_modules". Serve para guardar os arquivos de todas as dependências do seu projeto
- Um arquivo: "package-lock.json". Serve para guardar informações a respeito das versões das suas dependências

Essa parta e arquivos são sempre modificados/regenerados quando é executado o `npm install`, portanto você não precisa adicioná-los ao [[Git]].
# Dev Dependencies
O projeto também pode incluir dependências de desenvolvimento, as quais não são utilizadas em produção. Para incluir uma dependência de desenvolvimento, você pode digitar: 
- `npm install --save-dev`
- `npm install --save -D`

Uma dependência de desenvolvedor útil é a nodemon. Ela verifica se há mudanças no seu código ou dependências e restarta o servidor automaticamente. Depois de instalá-la (`npm install --save-dev nodemon`), adicionamos no package.json:
~~~json
"scripts": {
	"start": "node src/index.js",
	"dev": "nodemon src/index.js"
}
~~~
# ESM
Uma dependência que é muito útil para quem está acostumado com [[React-Native]], é a dependência "esm". Ela te permite usar import/export ao invés do padrão do NodeJS: require.
~~~js
const express = require('express');
module.export = mymodule

x

import express from 'express';
export mymodule;
~~~
Para se utilizar o esm, adiciona-se a seguinte linha no arquivo package.json:
~~~json
"type": "module"
~~~
Antigamente usava-se o esm atráves de script `start -r esm src/index.js`, mas ela é ultrapassada e não recomendada.
# Express
É uma dependência muita usada para criar [[Arquitetura Web|API]]'s em node, ela te permite implementar os métodos de uma API Rest:
- GET
- POST
- PUT
- DELETE
~~~js
const server = express();

server.get('/rota', (request ou req, response ou res) => {
	response.status(200).send('OK');
}); // Se alguém acessar o server com o método get na rota /rota

server.listen(3000, pode-se passar uma função para executar quando conectar);
~~~
Os métodos recebem como parâmetros a rota e uma função que lida com:
- Req: requisição HTTP
- Res: resposta HTTP

Depois deve definir uma porta para o servidor, por exemplo: 3000.

Para lidar com variáveis nas requisições usamos:
~~~js
const server = express();

server.get('/rota/:id', (req, res) => { // Usamos o : para indicar que é uma variável e aí colocamos o nome dela (id no caso)
		const id = req.params.id; // Para acessar a variável usa-se o req.params.nome
})
~~~
Para lidar com requisições do tipo POST:
~~~js
server.post('/alunos', (req, res) => {
	const name = req.body.name; // Com req.body acessamos o corpo e com .nome acessamos a parte do corpo do mesmo nome que foi especificado
	const age = req.body.age;
})
~~~
O código de status `202` é para quando foi criado.
Parou no minuto 34:34.