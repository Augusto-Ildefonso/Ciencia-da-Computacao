# Arquitetura Básica
A arquitetura básica da web consiste em três partes: front-end, back-end e base de dados.

O front-end é tudo que é rodado no computador/celular do cliente. Ele pode ser tanto um aplicativo, uma página web ou então um sistema. Algumas linguagens usadas para ele são: HTML, CSS, JavaScript, React, React Native.

O back-end é rodado no servidor ou nuvem. Geralmente se contrata algum serviço de hospedagem para poder hospedar o back-end no servidor. Um exemplo de linguagem para back-end é Nodejs. Ele recebe um HTTP request do cliente e retorna um dado para o cliente. Esse dado pode ser tão simples quanto carregar arquivos estáticos.

O banco de dados armazena os dados do sistema e dos clientes. Geralmente usa-se um servidor diferente do back-end, mas pode usar o mesmo. O back-end se comunica com o banco de dado. Alguns sistemas de gerenciamento de banco de dados (SGBDs) são: MongDB, Firebase, Postgres. MySQL.
# Modelo Antigo
O modelo antigo de sistemas web é: o cliente faz um HTTP request para o servidor, que recebe essa requisição e então procura os dados no banco de dados (essa consulta ao banco de dados lida com as lógicas de negócios (back-end que faz)). Ao encontrar o dado, essa é a parte que mais se diferencia para o modelo novo, ele cria um código HTML dentro do back-end e retorna esse arquivo, com os dados, para o cliente e o front-end apenas renderiza o HTML.
# Modelo Novo
O modelo novo de sistemas web é: o cliente faz um HTTP request para o servidor e o back-end procura os dados no banco de dados (essa consulta a base de dados lida com lógicas de negócios (back-end que faz)) retorna os dados apenas um arquivo JSON. A partir desse JSON, o front-end cria o HTML, através do JavaScript.
# JSON
É um formato de serialização de dados. Ele possui estruturas chamadas de objetos e listas.
Um objeto é estruturado da seguinte forma:
~~~JSON
{
	"chave1": "valor1",
	"chave2": "valor2"
}
~~~
E a lista é estruturada da seguinte forma:
~~~JSON
{
	"numeros": [1, 2, 3, 4]
}
~~~
# Comunicação Back-Front
É importante que exista uma padronização para o desenvolvimento do back-end. Assim, existem diversas formas de estruturar o back-end. Uma delas é estruturá-lo como API (Application Programming Interface) que é um conjunto de padrões para se desenvolver back-end e, ainda, há diversas formas de se desenvolver uma API, uma delas é a REST (Representational State Transfer), que é um conjunto de padrões para se desenvolver uma API.

Uma API é um conjunto de rotinas e padrões que uma aplicação disponibiliza para que outras aplicações possam utilizar as funcionalidades desta aplicação. Uma boa analogia é pensar em um restaurante, nele temos três personagens: cliente, garçom e cozinha. O cliente faz um pedido, o garçom recebe o pedido e leva os pedidos para a cozinha e dela para o cliente, a cozinha prepara o pedido. Trazendo para o contexto de API agora:
- Cliente: faz o papel do próprio cliente que requisita algum dado do servidor
- Garçom: faz o papel da API que recebe a requisição e leva ela para o servidor e retorna o dado para o cliente
- Cozinha: faz o papel do servidor que entrega o dado que o cliente requisitou

Os papéis de uma API são:
- responsável por estabelecer uma comunicação entre diferentes serviços
- meio de campo entre as tecnologias
- intermediador para troca de informações

Agora quanto ao REST, podemos novamente utilizar a analogia do restaurante. Quando você vai a um restaurante, você espera que ele seja limpo, que te atenda bem e entregue o que você pediu. Além disso, você, quanto cliente, não pode ficar gritando nem xingando, ou seja, foram definidas boas práticas. Isso é o REST, ele determina boas práticas, obrigações nas transferências de dados. Geralmente usa-se o protocolo HTTP para a transferência de dados. No REST chamamos os dados, objetos, entidades de resource (pode-se acessar um resource pelo endpoint de uma URL, o resource seria o bloco de notas do garçom). Há 5 (6*) obrigações/necessidades (constraints) para uma API ser RESTful (aplicar os padrões REST):
- client-server (cliente-servidor): os clientes e servidores devem ser separados. Tem que haver uma separação do cliente e do armazenamento de dados do servidor, dessa forma, poderemos ter uma portabilidade do nosso sistema, usando o React para WEB e React Native para smartphone.
- stateless (sem estado): cada requisição que o cliente faz para o servidor deverá conter todas as informações necessárias para o servidor entender e responder (response) a requisição (request). Um exemplo: a sessão do usuário deverá ser enviada em todas as requisições, para saber se aquele usuário está autenticado e apto a usar os serviços, e o servidor não pode armazenar que o cliente foi autenticado na requisição anterior.
- cacheable: as respostas para uma requisição devem ser explícitas ao dizer se aquela requisição pode ou não ser cacheada pelo cliente (se o dado pode ser guardado no cache*).
- layered system (sistema em camadas): o cliente pode acessar o endpoint (numa URL o endpoint é o que vem depois da "/", exemplo: https:.//graph.facebook.com/youtube, esse "/youtube" é um endpoint), sem precisar saber da complexidade por trás, de quais passos estão sendo necessários para o servidor responder a requisição, ou quais outras camadas o servidor estará lidando, para que a requisição seja respondida.
- code on demand (opcional): dá a possibilidade da nossa aplicação pegar códigos, como o javascript, e executar no cliente.

Algumas boas práticas são:
- Usar verbos HTTP (GET: receber dados de um resource , POST: enviar dados ou informações para serem processador por um resource, PUT: atualizar os dados de um resource, DELETE: deleta um resource)
- Utilizar ou singular ou plural na criação de endpoint? Não importa, mas manter o padrão que escolher
- Não deixar "/" no final do endpoint
- Nunca deixe o cliente sem respostas

Alguns status de respostas para informar o cliente são:
- 1xx: Informação
- 2xx: Sucesso
	- 200: OK
	- 201: CREATED
	- 204: Não tem conteúdo PUT, POST, DELETE
- 3xx: Redirection
- 4xx: Client Error
	- 400: Bad Request
	- 404: Not found
- 5xx: Server Error
	- 500: Erro interno do servidor
# HTTP Request
É quando você manda o que você quer para o servidor. O cliente cria uma requisição (request) usando o protocolo HTTP e manda ela para o servidor. A estrutura de um HTTP Request é:
- Host
- Rota
- Método
- Headers
- Body (informações que quer passar)

Acessar uma URL é fazer um request. Destrinchando uma URL, exemplo: https://www.youtube.com/watch?v=ghTrp1x_1As&t=83s.
- HTTPS - Protocolo HTTP + Secure (S)
- www.youtube.com - HOST, identifica o computador em que o youtube está hospedado
- /watch - Caminho (rota) dentro do site do youtube
- ? - Indica que vai começar a referenciar variáveis
- v=ghTrp1x_1As - Indica o valor para a variável v
- & - Indica que vai colocar outra variável
- t=83s - Indica o valor para a variável t
- Método padrão - GET
# Softwares de Teste
Softwares de teste de API permitem fazer requisições HTTP e observar as respostas. Dois softwares de teste são: [Postman](https://www.postman.com/) e [Insomnia](https://insomnia.rest/download).