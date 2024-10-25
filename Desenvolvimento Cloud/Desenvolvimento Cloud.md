# Conceitos da Cloud
## O que é Cloud Computing
Cloud Computing são serviços e recursos de computação oferecidos por uma empresa através da internet. Segundo o NIST, Cloud Computing tem como características:
- Poder provisionar capacidade computacionais conforme necessário sema  obrigatoriedade de interação humana
- Capacidades computacionais estarão disponíveis através da internet, atendendo aos mecanismos padrões de redes
- Localização independente, ou seja, sem controle ou conhecimento exato de onde estão localizados os recursos, e os mesmos serão oferecidos em um modelo de locação
- As capacidades podem ter provisionamento elástico e uma escala rápida conforma a demanda, além de oferecer um provisionamento muito parecido com recursos limitados
- Utilização der recursos pode ser monitorada, controlada, reportada e cobrada financeiramente
## Players e CSP
São os provedores do serviço de Cloud Computing. Alguns exemplos de provedores/players são:
- AWS (Amazon)
- Azure (Microsoft)
- Google Cloud
- Oracle Cloud
- IBM Cloud
- Alibaba Cloud
- Huawei Cloud
## IaaS, PaaS e SaaS (FaaS)
- IaaS (Infrastructure): Infraestrutura como Serviço (Infrastructure as Service). Sua característica é uma maior participação humana, a AWS só da a ferramenta, mas o processo é por conta de alguém. O ser humano tem uma maior responsabilidade e também uma maior personalização. No IaaS é necessário montar as aplicações, dados, runtime, middleware e o sistema operacional.
- PaaS (Plataforma): Plataforma como Serviço (Plataform . Ele possui uma menor participação humana, o AWS já dá uma estrutura que somente é necessário ligá-la e mexer em poucas configurações. No PaaS é necessário montar a aplicação e os dados
- SaaS (Software): Software como Serviço. Possui uma menor participação humana (menos que o PaaS), só escolhemos qual serviço usar e ele já faz todo o processo necessário. O ser humano tem uma menor responsabilidade, mas também tem uma menor personalização, vai depender de quais serviços estão disponíveis. No SaaS não é necessário montar nada
- FaaS (Function): Função como Serviço. Permite rodar códigos/funções no servidor, não é de fato um produto, um software. No FaaS não é necessário montar nada e ele ainda oferece o código para fazer as funções. Exemplo é o Lambda.

Pode-se traçar uma analogia com o processo de fazer café. A IaaS seria o equivalente a fazer um café coado, você só tem uma infraestrutura, mas todo o processo é por conta do homem. A PaaS seria um café de cápsula, então não é necessário tanta intervenção humana, só é necessário ligá-la e colocar a cápsula, escolher a quantidade de água (poucas configurações). Por último o SaaS é o equivalente a pedir um café no starbucks, você não faz nada, só escolhe o sabor (serviço), só que o problema disso é que você fica a mercê do que tem lá (dos serviços que oferecem).

Além disso, antes da existência de computação em nuvem, o que ocorria era o "On Premises", que seria montar todo o servidor, ou seja, teria que montar: aplicações, dados, runtime, middleware, OS, virtualization, servidores, armazenamento, redes. Adendo, um servidor é basicamente um computador, qualquer computador pode servir de servidor (mas nem por isso todo computador deve ser usado para isso).

Atenção, não é recomendado usar a conta root para fazer operações na AWS. Outro alerta, cada região tem um valor no AWS, recomendado a Vírgínia por ser a mais barata.
# Amazon Web Services (AWS)
A AWS possui mais de 200 serviços, em praticamente todas as áreas.
## Alta Disponibilidade
Os provedores colocam os data centers em posições diferentes dentro de uma mesma região.

Algumas estratégias para conseguir uma alta disponibilidade de serviços são:
- Multi-AZ Deployments: estamos em uma região, que tem várias zonas. Então se algo afetar uma zona, não cairá o serviço pois terá outras
- Load Balancing: é um tipo de arquitetura que faz a distribuição de carga
- Auto Scaling: consegue escalar de forma automática. Então se precisar aumentar a capacidade, ela vai fazer automaticamente
- Fault Tolerance (região): é tipo o multi-az mas para regiões
- Data Replication: ter os mesmos dados em várias regiões
- Disaster Recovery
- Service-Level Agreements (SLAs): frequentemente 99,99% ou mais
- Monitoring and Alerts: como Amazon CloudWatch e AWS
- Arquiteturas distribuídas
## Tags
As tags são uma forma de organização do serviço, são labels/etiquetas para os recursos. Podemos trabalhar com arquiteturas baseadas nas tags.
## Serviços
### EC2 e EBS
O EC2 são máquinas virtuais, dentro do mundo da cloud chamamos essas máquinas de instâncias. Temos vários tipos de instâncias: processamento (vCPU) (intel, AMD ou graviton), memória RAM, instance storage, rede. Existem também as famílias para que possamos utilizar as instâncias com alguns focos específicos: geral (m), computing (c), memory (r) e storage (i).

No AWS, os custos desse serviço são por hora (MAC e Windows, Linux é por segundo), por tipo e tamanho de instância, e por "pacote": "On-demand" (de acordo com a demanda, mais caro que a reservada pois não dá garantia à AWS que será usado por tanto tempo), Spots (é como se fosse um leilão, são instâncias que não são usadas no momento e por isso são bem baratas, mas a AWS pode tirar a qualquer momento de você, com um período de 5 min de aviso) e Reservadas (fecha um tipo de contrato de por quanto tempo vai usar a instância, pode ser que não use durante todo esse período, por isso é barato) ou Saving Plans.

Outros custos além da própria instância são: transferência de dados e disco.

Já o EBS são discos anexados à instância, os tipos comuns são GP2 e GP3. O EBS é uma instância só de armazenamento, diferente do Instance Storage (instância de armazenamento, que é um computador todo com foco para armazenar).
## Auto Scaling
É a estratégia de ajustar a sua capacidade de forma automática, conforme a demanda. Porém ainda sim é necessário estipular um limite máximo e mínimo. Escalabilidade vertical é quando aumenta a capacidade do mesmo computador (como se aumentasse o HD, a memória, etc.), já escalabilidade horizontal é quando aumenta a capacidade aumentando o número de instâncias (antes tinha um, agora vai ser mais de um, as vezes isso sai mais barato), nesse caso de escalabilidade horizontal é necessário um load balance.

Geralmente usa-se a escalabilidade horizontal, por isso tem que definir um número mínimo de instâncias que ele irá usar e, também, o número máximo de instâncias. Ela pode ser tanto para cima (aumenta o número de máquinas) ou para baixo (número mínimo). Além disso, pode-se estabelecer um threshold, uma porcentagem de CPU ou memória que quando atingir, também vai realizar o auto scaling.

Para decidir se irá escalar ou não a máquina temos alguns métodos:
- Baseado em métricas de utilização, que podem ser agendadas ou então baseadas em outras métricas como dados e utilização.
## RDS 
Ele é um serviço de banco de dados relacional. A ideia dele é que ele seja uma plataforma, na qual só escolhemos o "tipo". Ele é um PaaS de banco de dados. Também é possível fazer reservas de instâncias. As vantagens são:
- Versões suportadas (updates mais fáceis)
- Licenciamento (usando o seu ou "alugando" um)
- Alta disponibilidade
- Gerenciamento
	- Monitoria
	- Backup

Quando um serviço é dito gerenciado significa que eles trabalham mais neles.

Amazon Aurora, é muito parecido com um RDS, mas pode ser usado como uma engine/serviço de alta performance e disponibilidade. Ele é compatível com MySQL e PostgreSQL, ele tem opção do tipo serverless (o serverless é um método de prover serviços "On-demand", seja de processamento, memória, armazenamento, etc; ele vai pegar máquinas conforme precisa), até 15 endpoints de leitura e é cobrado pelo armazenamento utilizado.
## S3
É um serviço de armazenamento de objetos:
- Imagens
- Vídeos
- Arquivos Gerais

Esse serviço é escalável, durável, acessível na internet, seguro e de baixo custo.
# Desenvolvimento na AWS
## IaC
Infrastructure as Code, ou, Infraestrutura como código. O CloudFormation é um serviço da amazon que permite tratar as infraestruturas como código. Ele é tipo um terraform (só que o terraform é genérico). As outras clouds também tem: ARM Templates (Azure), CDK (AWS). As vantagens de usar uma IaC são:
- Evita o desvio ao sempre fornecer o mesmo ambiente
- Desenvolvimento mais rápido e eficiente
- Padronização
## SAM
O SAM (serverless application model) é uma ferramenta que server para fazer o gerenciamento das aplicações em server. Ele faz templates que podem ser rodados direto na máquina de desenvolvimento. Ele faz a implantação do CloudFormation (por baixo dos planos, sem que a gente veja) e faz o deploy de maneira automáticas. Ele faz o gerenciamento de lambda e age como um API Gateway. Ele também permite a execução local (docker).
## CodeCommit
É um serviço de GIT da AWS, mas que não deu certo e vai ser descontinuado. O Git serve para fazer o:
- Versionamento
- Branches
- Commits
- Pull Requests/Merge Requests
## CI/CD
Continuous Integration (CI), ou integração contínua, vem para poder jogar o código no git de maneira saudável, ele cria as esteiras de testes, segurança e integração. Já o continuous delivery, ou entrega contínua, usa branches, implementação da solução, validações antes de subir para produção, subida automática, rollback mais rápido. A vantagem de usar CI/CD é que garantimos, pelo CI, que o que estamos subindo está funcionando, saudável, (mas claro que podem ter bugs ainda), e pelo CD, ele vai fazer o deploy automatizado.

Como fazemos o DevOps dentro da amazon:
- Pipelines: são arquivos de configurações e etapas
- Execução das validações e build: feitas com máquinas temporárias ou de execução única.

Os serviços são:
1. CodeCommit (Vai ser descontinuado)
2. CodeDeploy
3. CodeBuild
4. CodePipeline

Nos concorrentes é feito com: GitHub Actions, Azure DevOps, GitLab, Jenkins.
# Criando o front-end
1. Ir no CloudFormation e criar uma pilha, usando como base um yml
2. Ir no S3, acessar nosso bucket e fazer upload de um html
3. Depois ir no cloud front e mudar o invalidation para /* para limpar o cache