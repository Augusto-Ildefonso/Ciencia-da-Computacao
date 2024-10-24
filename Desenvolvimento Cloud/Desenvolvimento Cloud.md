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
