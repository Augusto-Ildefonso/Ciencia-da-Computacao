# Introdução
A internet é uma rede global de redes que conecta milhões de dispositivos através de: email eletrônico, compartilhamento de arquivos (FTP), jogos online, aplicativos mobile, páginas web, etc.
Já Web (World Wide Web) representa um conjunto de informações acessadas via internet por meio de hyperlinks (referenciando URLs (Uniform Resource Identifier)). Ou seja, a web é uma das redes presentes na internet. Os recursos presentes na web são acessados por meio de navegadores fazendo o uso do protocolo HTTP ou HTTPS.
Os recursos na web costumam ser apresentados na forma de webpages - que formam websites.
## Arquitetura
Em uma aplicação Web, há dois tipos de "sub-programas", um _client-side_ e outro _server-side_. O código _client-side_ (HTML, CSS e Javascript) é o que está na página do navegador e que interage diretamente com as entradas do usuário. Já o código _server-side_ está em um servidor e responde às requisições HTTP que chegam até ele. Para o código _server-side_, pode-se utilizar C#, Java, Javascript, Python, PHP, Ruby e mais - basicamente, qualquer linguagem que entenda e responda requisições HTTP.
# Protocolo HTTP
É a base de troca de dados da internet. Ele é o responsável por transmitir HTML's, imagens, vídeos e resultados de formulários entre cliente e servidor.

O HTTP é um protocolo stateless (comunicação feita por meio de mensagens individuais) cliente servidor que segue o seguinte modelo de comunicação: um cliente (geralmente o browser) abre uma conexão por meio de uma requisição feita ao servidor, que recebe a requisição e envia uma resposta ao cliente. Vale ressaltar que essa comunicação não é "direta" como parece ser ao descrever, entre o cliente e o servidor existem vários dispositivos tratando e retransmitindo a mensagem.
## Etapas de comunicação - Fluxo
A comunicação ocorre por meio de mensagens individuais. Quando um cliente quer se comunicar com o servidor ele segue os seguintes passos:
1. Abrir uma conexão TCP: essa conexão é utilizada para enviar uma ou várias requisições e receber respostas
2. Enviar mensagem HTTP: um detalhe do protocolo HTTP é que essa mensagem não é criptografada, ou seja, ela pode ser lida por qualquer um que esteja monitorando o fluxo de pacotes da rede. O padrão da mensagem é: ![Imagem](https://gitbook.ganeshicmc.com/~gitbook/image?url=https%3A%2F%2Fi.imgur.com%2FOxDXcP7.png&width=768&dpr=1&quality=100&sign=c2628093&sv=1)
3. Ler a mensagem de resposta do servidor: após enviar uma requisição, se não houver problemas, o servidor enviará uma resposta. Essa resposta também não é criptografada e segue esse padrão.
4. Fechar ou reutilizar a conexão TCP que foi aberta