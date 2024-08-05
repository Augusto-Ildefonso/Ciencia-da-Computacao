Git é sistema de controle de versão. Ele foi criado em 2005 por Linus Torvalds e está sendo mantido por Junio Hamano desde então. Ele serve para:
- Acompanhar mudanças no código
- Acompanhar quem fez mudanças no código
- Colaborar com códigos
# O que ele faz
- Gerencia projetos com Repositórios
- Clona um projeto para trabalhar em uma cópia local
- Controla e acompanha mudanças com Staging e Commiting
- Branch e Merge para permitir trabalhar em diferentes partes e versões do projeto
- "Pull" a último versão do projeto para uma cópia local
- "Push" mudanças locais para o projeto principal
# Trabalhando com o git
1. Inicialize o git em uma pasta, isso o tornará um Repositório
2. O git então cria uma pasta "escondida" para acompanhar as mudanças naquela pasta
3. Quando um arquivo é criado, modificado ou deletado, é considerado modificado
4. Você seleciona os arquivos modificados que quer Stage
5. Os arquivos Stage são Committed, o que faz com que o git armazene snapshots permanentes dos arquivos
6. O git permite ver todo o histórico de commits
7. Você pode voltar para qualquer versão de commit
8. O git não armazena uma cópia de cada arquivo em cada commit, ele armazena as mudanças feitas em cada commit
# Git vs Github
- Github faz ferramentas que usam o git
- O github é o maior host de código fonte do mundo
# Arquivos Novos
Ao criarmos um arquivo e usarmos o git status, podemos ter dois tipos de arquivos:
- Tracked: arquivos que o Git conhece e estão adicionados no repositório
- Untracked: arquivos que estão no diretório atual, mas não estão adicionados no repositório
Quando acaba de criar um novo arquivo no repositório ele é do tipo untracked, para torná-lo tracked temos que realizar o Stage ou adicioná-los ao staging enviroment.
# Staging Enviroment
O conceito de Staging Enviroment e Commit é uma função principal do git.
Ao alcançar metas no desenvolvimento dos códigos, devemos adicioná-los ao Staging Enviroment. Arquivos Staged são arquivos que estão prontos para serem committed para o repositório que está trabalhando.
Se usar o --all para adicionar os arquivos, todas as modificações (criação, mudança e deleção de arquivos) será adicionadas ao Staging Enviroment.
Não é recomendado pular esse estágio pois pode-se adicionar mudanças indesejadas.
# Commit
Após adicionar os arquivos ao Staging Enviroment, está na hora de realizar o commit deles. Ao realizar commits, podemos acompanhar o progresso e as mudanças do código conforme trabalhamos.
O git considera cada commit um "save point", ou seja, um ponto para o qual é possível retornar se encontrar algum bug ou quiser fazer uma mudança.
Quando realizar commit, deve sempre adicionar uma mensagem, clara, para facilitar a compreensão do que mudou e quando mudou.
As vezes, ao realizar pequenas mudanças, usar o Staging Enviroment pode ser perda de tempo. Então podemos realizar o commit pulando o Stage os arquivos. Para isso usa-se a flag -a.
# Branch
Uma branch é uma nova e separa versão do repositório principal. Branches permitem trabalhar em diferentes partes do projeto sem impactar na branch principal. Quando terminar o trabalho na branch, pode realizar o merge dela com o main e ai juntar a mudança na main.
Quando estamos em uma branch, todas as mudanças, Stage e commit que fizermos serão para aquela branch e não para a main.
Porém, haverá um problema quando for realizado um merge de uma branch B depois de já ter sido criada a branch A. Isso gerará um conflito entre as duas versões do arquivo que foi modificado.
# Merge
Irá juntar a branch criada com a master. Para isso, precisa primeiro estar na master branch. Se realizar um merge direto da master e nenhuma outra mudança foi feita a master branch enquanto estava em outra branch, o git vê o merge como uma continuação da master. Então ele "fast forward", e aponta ambas a master e a outra branch para o mesmo commit. E como nesse caso a master e a outra branch são praticamente a mesma branch, podemos deletar a outra branch.
# Adicionando o repositório local ao GitHub
Ao rodar os comandos listados abaixo, irá se deparar com um problema, se usar o método http: ele irá pedir a senha do usuário mas se colocá-la dará erro, isso pois a autenticação por senha foi removida. Sendo assim, é necessário agora, no lugar da senha, colocar o [personal acess token](https://docs.github.com/pt/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens) ou usar um auxiliar de credenciais, como o [gerador de credenciais do git](https://github.com/GitCredentialManager/git-credential-manager/blob/main/README.md).
## Personal Acess Token
Ele é usado como uma forma alternativa ao uso de senhas para acessar os recursos do Github pela linha de comando ou API do Github. Esse token é usado para acessar o Github em nome de si mesmo. Existem dois tipos de tokens: fine-grained e classic.
O fine-grained tem várias vantagens de segurança em relação ao classic.
Já o classic é menos seguro, mas possui alguns recursos que só funcionam com ele (acesso a gravação em repositórios públicos).
O uso de tokens no entanto é menos seguro do que o uso de gerador de credenciais, pois o token compartilha os mesmos riscos de senha.
# Pull
Ele é usado para puxar as mudanças mais recentes do repositório remoto para o repositório local usamos o pull. Ele é a junção de 2 comandos: fetch e merge.
Então se não quisermos realizar os comandos acima, podemos simplesmente usar o comando pull
# Fetch
Fetch puxa todo o histórico de mudanças de um repositório tracked. Pode-se rodar o git status depois do fetch para ver se tem alguma mudança. Após verificar as mudanças entre a origem e o nosso repositório local, podemos fazer o merge.
# Push
Empurramos as mudanças feitas nos arquivos para a origem.
# Pull branch do Github
Para puxar uma branch do Github, primeiro temos que dar um pull para que o repositório local esteja em dia. Segundo, usamos o checkout para ir para a branch do repositório remoto. Terceiro, damos um pull nela para garantir que está em dia. Assim terremos feito o pull de uma branch. Se não fizer o checkout, ao rodar branch, verá que não existe a branch no repositório local e por isso é necessário fazer o checkout.
# Push branch para o Github
É só usar o comando push junto da branch que quer empurrar.
# Github Flow
O Github flow é um workflow pensado para funcionar bem com git e github. Ele foca em fazer branches e tornar possível para times experimentar livremente e fazer deploys regularmente.
O Github flow funciona do seguinte jeito:
1. **Cria-se uma nova branch**
	A ideia é de que a branch master sempre tem que ser deployable (possível de ser lançada/publicada). Então se quiser experimentar ou criar algo novo deve-se criar uma nova branch. As branches dão um ambiente que permite experimentar sem afetar a branch principal. 
	Quando a branch estiver pronta, ela pode ser revisada, discutida e aí ser feito um merge dela. 
	Quando se cria uma branch, quase sempre, quer que ela seja feita da branch principal.
	Vale notar que como sempre estamos trabalhando com outras pessoas, é bom usarmos nomes descritivos para as branches.
2. **Faça mudanças e adicione commits**
	Agora que o ambiente está pronto é hora de realizar mudanças no código e arquivos. Sempre que atingir algum ponto importante, faça o commit da sua branch. Fazer commits mantém um histórico do seu trabalho. Toda commit deve ter uma mensagem do que ser feito e por que. Vale lembrar que sempre pode voltar para alguma commit antiga.
3. **Abra um pull request**
	Pull request são uma parte fundamental do Github. Elas mostram para as pessoas que você tem mudanças prontas para serem revisadas e consideradas. Você pode pedir para os outros reverem suas mudanças e fazer o merge das suas mudanças para a branch deles.
4. **Revise**
	Quando uma pull request é feita, ela pode ser revisada por qualquer um que tenha acesso à branch. É nesse momento que boas discussões e revisões podem ser feitas. As pull requests foram feitas para permitir as pessoas trabalharem juntas facilmente e produzirem melhores resultados. O Github mostra as novas commits e o feedback na aba "unified pull request view".
5. **Deploy**
	Após ser revisada e verificada, é hora do teste final da pull request. O Github permite que você faça o deploy de uma branch para o teste final na produção antes de fazer o merge com a branch principal. Se qualquer problema aparecer, você pode desfazer as mudanças, fazendo o deploy da master branch para produção de novo.
	Times geralmente tem um ambiente de testes dedicado para fazer o deploy de branches.
6. **Merge**
	Depois de testada, pode-se fazer o merge do código na branch principal. Você pode adicionar palavras chaves às pull requests para pesquisar mais facilment.
# Github Pages
Com o Github Pages, o Github permite você hostear uma página web a partir do seu repositório.
Para criar o repositório que será usado como página, o nome dele tem que ser: seuusuário.github.io.
Em seguida é necessário fazer o push do seu repositório local para o Github.
Então verifica se os arquivos apareceram e, assim, pode ir para a aba do Github Pages e achará o link do site.
Acredito que tenha como criar o Github Pages de outros repositórios, mexendo na aba do Github Pages.
# Contribuindo com repositórios
O coração do Git é a contribuição, porém o git por si só não permite fazer mudanças ao código de outros sem a autorização necessária. Mas tem como fazer essas mudanças. Vale ressaltar que nesse processo, pode ser que ao fazer o fork não consigamos rodar os comandos porque falta permissão, para resolver isso é só executá-los como sudo.
## Fork
A ideia do fork é copiar o repositório. Isso é útil quando se quer contribuir com o projeto de alguém ou então usá-lo como base para o seu projeto.
Fork não é um comando disponível no Git, mas um recurso que o Github disponibiliza, assim como outros hosts de repositórios.
Para realizar o Fork basta clicar no botão Fork para copiá-lo para o seu perfil.
## Clonando um Fork do Github
Um clone é uma cópia completa de um repositório, incluindo todas os logs e versões de arquivos.
Primeiro, no botão Code, copiamos a URL do repositório que queremos clonar.
Então precisamos configurar os remotes, porque temos uma cópia completa de um repositório, cuja origem não temos permissão para mudar. Então vemos como os remotes do git estão configurados:
```
$ git remote -v
```
Assim vemos qual o nome do repositório original, assim queremos adicionar nosso próprio Fork. Então nós renomeamos o original `origin remote`:
```
git remote rename <original> <novo>

Exemplo:

git remote rename origin upstream
```
Então fazemos a fetch do nosso próprio Fork, usando o comando:
```
git remote add origin <url do fork>
```
De acordo com as convenções do Git, recomendam chamar o nome do seu repositório de origin e o que você fez o fork upstream.
Agora vamos ter dois remotes:
- origin - nosso própio fork, onde temos permissão de ler e escrever
- upstream - o original, onde temos permissão de leitura somente
Após ter adicionado o nosso Fork, faremos a mudança no código e em seguido realizaremos o add e commit dele. E por fim faremos o push
## Enviando um Pull Request
Após feitas as mudanças, devemos fazer um push delas para o nosso fork:
```
$ git push origin
```
Então, com o push feito, podemos entrar no nosso fork e ver que tem uma notificação de que um branch fez um commit, clicamos no aviso e colocamos que queremos fazer um pull request no repositório original. Assim escrevemos nossa mensagem e comentário e por fim pedimos o pull request. Agora basta alguém que tenha acesso aceitar.
# Git Ignore
Quando compartilhamos o código, podem ter partes do projeto que não queremos que sejam compartilhadas, como: 
- arquivos log
- arquivos temporários
- arquivos ocultos
- arquivos pessoais
- etc
Para isso, podemos dizer para o git quais arquivos ou partes do projeto devem ser ignorados usando o arquivo .gitignore. O Git não vai acompanhar os arquivos listados no .gitignore, mas ele irá acompanhar o arquivo .gitignore.
Para criar o arquivo vamos até a raíz do repositório e executamos:
```
$ touch .gitignore
```
Então abrimos ele com o editor de texto e adicionamos as regras para mostrar quais arquivos ignorar.
Vale mencionar que podemos criar .gitignore em subdiretórios para que eles tenham um escopo daquele diretório, se criarmos na raíz ele terá o escopo do repositório.
O .gitignore funciona com regras, elas podem ser vistas nesse [link](https://www.w3schools.com/git/git_ignore.asp?remote=github).
É possível ignorar arquivos e pastas e não mostrar no .gitignore que será distribuído. Essas regras vão ser mostradas no arquivo `.git/info/exclude`. Ele funciona do mesmo modo que o .gitignore mas não é mostrado para ninguém.

# Comandos
### Versão do git
```
$ git --version
```
## Configurando o git
```
$ git config --global user.name "nome do usuário"
$ git config --global user.email "email"
```
Usamos o --global para configurar esse nome e email para todo repositório no computador. Para configurar esse nome e email apenas para o repositório atual é só remover o --global.
## Inicializando o git
```
$ git init
```
Nesse momento o git cria uma pasta oculta para acompanhar as mudanças.
## Verificando status do git
```
$ git status
```
É usado, por exemplo, após adicionar um novo arquivo para poder ver se o git reconheceu ele, se ele foi adicionado para o staging enviroment.

```
$ git status --short
```
Usando a flag --short as mudanças serão mostradas de um jeito mais compacto. As flags que aparecem quando se usa o --short são:
- ?? - Untracked files
- A - Arquivos adicionados ao Stage
- M - Arquivos modificados
- D - Arquivos deletados
## Adicionando um arquivo ao Staging Enviroment
```
$ git add <file>
```
Pode-se usar o --all ou -A no lugar do nome do arquivo para adicionar todos os arquivos do diretório ao Staging Enviroment.
## Fazendo commit
```
$ git commit -m "mensagem"
```
O -m permite escrever a mensagem.

```
$ git commit -a -m "mensagem"
```
A flag -a realizar automaticamente o Stage dos arquivos, tornando-os tracked files.
## Log do commit
```
$ git log
```
Esse comando permite ver o histórico de commits do repositório.

```
$ git log origin/master
```
Esse comando permite ver o histórico de commits da origem no branch master.
## Help
```
$ git command -help
```
Esse comando permite ver as opções de cada comando. Pode-se usar também --help, que irá abrir a página de manual do git.

```
$ git help --all
```
Esse comando listará todos os comandos possíveis do git. Se estiver querendo pular para o fim da lista pode-se usar o ctrl + G e em seguida o "q" para sair da visão da lista. 
## Branch
```
$ git branch nome-da-branch
```
Esse comando cria uma nova branch.

```
$ git branch
```
Ele vai listar todas as branchs criadas. O asterisco mostrará em qual branch estamos.

```
$ git checkout nome-da-branch
```
Irá nos mover para a branch especificada.

```
$ git checkout -b nome-da-branch
```
Será criada uma nova branch com o nome fornecido e você será movido para ela.

```
$ git branch -d nome-da-branch
```
Essa flag deleta a branch especificada.

```
$ git branch -a 
```
Essa flag permite ver todas as branchs disponíveis, local e remota.

```
$ git branch -r
```
Essa flag permite ver as branchs remotas.
## Merge
```
$ git merge branch-com-a-qual-queremos-juntar
```
Faz o merge da branch especificada com a branch que está.

```
$ git merge origin/master
```
Faz o merge da origem no branch master com o branch do repositório local.
## Dando push do repositório local para o Github para colocar o Github como origem
```
$ git remote add <nome que será dado, exemplo: origin> <url>
```
Esse comando especifica que está adicionando um repositório remoto, com a url especificada, como a origem para o seu repositório local

```
$ git push --set-upstream origin master
```
Esse comando faz o push da master branch para a origem (repositório remoto) e seta ele como a branch remota padrão.
## Fetch
```
$ git fetch origin
```
Esse comando puxa o histórico de mudanças da origem.
## Diff
```
$ git diff origin/master
```
Esse comando mostra a diferença entre o branch especificado e o branch que estamos.
## Pull
```
$ git pull origin
```
Esse comando puxa as mudanças da origem e faz o merge delas com o repositório local.
## Push
```
$ git push origin
```
Esse comando empurra as mudanças da branch que estamos para a origem.

```
$ git push origin branch-que-esta
```
Esse comando empurra as mudanças da branch especificada para a origem. Ele também é usado para empurrar uma branch para a origem.
## Clone
```
$ git clone url diretório
```
Esse comando permite clonar um repositório do Github, ele já criará um diretório para o código. Podemos especificar o diretório que queremos se colocarmos o nome do diretório após a URL, mas não é obrigatório