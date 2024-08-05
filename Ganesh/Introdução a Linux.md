# O que é um sistema operacional

O sistema operacional do computador é um software responsável por realizar a comunicação entre o hardware e os demais softwares do computador.

Sua função é administrar e gerenciar os recursos do sistema, desde elementos de baixo nível (os componentes de hardware) até os de alto nível (programas de terceiros e interfaces gráficas), fornecendo uma interface entre o usuário e o hardware.

Entre as funções do sistema operacional podemos citar:
1. Gerenciamento de processos (execução de programas)
2. Gerenciamento de memória
3. Gerenciamento de recursos
4. Entrada/Saída de dados
5. Sistema de arquivos
6. Definir interface com o usuário
7. Tratamento de Erros

Interfaces de uso:
- Interface Gráfica (GUI)
- Interface de Terminal (CLI)
- Interface Textual 
- Interface de Voz (VUI)
# Utilizando a linha de comando (CLI)
Todos os comandos estão no formato: ==comando -flags argumentos==
## Comandos para ajuda e documentação
- man comando -> manual com informações acerca de todos os comandos
- info -> outra ferramenta de documentação
- uname -> mostra informações do sistema
## Comandos de controle e acesso
- exit -> termina a sessão, ou seja, a shell
- logout -> desloga/termina a sessão atual
- passwd -> muda a senha do usuário logado
## Comandos para gestão de arquivos e diretórios
- ls diretório -> listar o conteúdo de um diretório. A flag -l exibe o resultado em forma de lista e a flag -a exibe também o conteúdo oculto
- cd diretório -> mudar o diretório atual
	- / -> vai para o diretório root
	- ~-> vai para o diretório home
	- .. -> vai para o diretório anterior
- pwd -> mostra o diretório atual
- touch arquivo -> cria arquivo
- cp arquivo1 arquivo2 -> copia o conteúdo do arquivo1 para o arquivo2 (se o arquivo2 já existe, ele é sobrescrito)
- cat arquivo -> mostra o conteúdo de um arquivo e pode ser usado também para concatenar arquivos. Por exemplo, usando "a.txt b.txt > c.txt" juntamos o conteúdo dos arquivos a.txt e b.txt em um único arquivo chamado c.txt
- mv -> move ou renomeia arquivos ou diretórios
- mkdir diretório -> cria um diretório
- rm -> remove um arquivo ou diretório (para diretório usa a flag -r ou -R para remover recursivamente (remover os arquivos de dentro deles))
- rmdir diretório -> remove um diretório
- chmod -> muda as permissões de arquivo ou diretório. O formato que aparece no terminal as permisões são: user:group:everyone
	- 4 : read(r)
	- 2 : write (w)
	- 1 : execute (x)
- file -> determina um tipo de arquivo
- grep 'pesquisa' arquivo -> procura por um padrão em um arquivo
- strings -> retorna as strings identificadas em um arquivo
- unzip -> ferramenta para descompactar arquivos zipados
## Comandos para edição de texto
- emacs -> editor de texto
- nano -> editor de texto
- vim -> editor de texto do terminal
## Comandos de rede
- ping -> pingar um determinado host ou verificar existência de conexão. Ele envia pacotes icmp para o host especificado e mede o tempo de resposta, entre outras coisas
- ifconfig -> configurar a interface de uma rede. Utilizado para visualizar os ips da nossa máquina
- ssh -> cria sessão segura (secure shell) e permite nos conectar num servidor remoto através do protocolo ssh
- netcat -> cria conexão TCP/UDP
- netstat -> mostra o estado da rede
- nmap -> ferramente de port-scan para visualização de portas abertas num dado host
## Comandos de processos
- ps -> mostra os processos em execução
- pstree -> mostra processos atuais em forma de árvore
- kill -> mata um processo
## Comandos de informação de estado
- date -> exibe data e hora
- whoami -> diz quem é o dono da shell
- who -> mostra quem está logado no sistema

# Links
- https://www.rs-online.com/designspark/an-intro-to-linux-file-system-management
- https://youtu.be/26QPDBe-NB8
- https://youtu.be/o8NPllzkFhE
- https://cheatography.com/davechild/cheat-sheets/linux-command-line/pdf/
- https://www.openvim.com/tutorial.html
- https://overthewire.org/wargames/bandit/
- https://cmdchallenge.com/