# Introdução
## O que são paradigmas de programação
Os paradigmas de programação referem-se a diferentes estilos e abordagens para escrever código.
Entre os mais conhecidos estão o procedimental, orientado a objetos, funcional e lógico.
## Paradigmas de programação
Os paradigmas de programação podem ser categorizados em dois grupos principais: imperativo e declarativo. A categoria imperativa inclui os paradigmas procedural e orientado a objetos, enquanto a categoria declarativa inclui outros paradigmas como programação funcional e lógica.
## Paradigma procedural
O paradigma procedural é um estilo de programação que se concentra em procedimentos ou funções, em que sequencias de comandos são executadas para atingir um resultado. As linguagens C, Pascal e Basic são exemplos de linguagens de programação procedurais.
## Paradigma orientada a objetos
O paradigma orientado a objetos modela um sistema em termos de objetos, que são instâncias de classes que interagem entre si. Alguns princípios dela são: encapsulamento, herança, polimorfismo e abstração são fundamentais para este paradigma. Exemplos de linguagens são: Java, Python, C++ e C#.
## Paradigma funcional
O paradigma funcional se baseia no uso de funções puras e imutabilidade de dados, priorizando a expressão de lógica matemática na programação.
A recursão e a composição de funções são características essenciais desse paradigma, promovendo a modularização e o reuso de código.
Ela tem um foco forte na descrição de comportamento e na minimização de efeitos colaterais torna o funciona adequado para ambientes concorrentes e distribuídos.
Exemplos de linguagens são: Lisp, Haskell e Scala.
## Paradigma lógico
As linguagens principais são Prolog, Datalog, Answer set Programing. Ele tem uma abordagem baseada em lógica matemática e regras de inferência. Ela trabalha com resolução de problemas a partir de fatos, regras e consultas.
## Vantagens e desvantagens de cada paradigma
### Procedural
Vantagens:
- Simplicidade e controle preciso
Desvantagens:
- Dificuldade em lidar com sistemas complexos
### Orientado a objetos
Vantagens:
- Reutilização de código e modelagem do mundo real
Desvantagens:
- Overhead e curva de aprendizado
### Funcional
Vantagens:
- Imutabilidade e facilidade de paralelização
Desvantagens:
- Dificuldade de compreensão para iniciantes
### Lógico
Vantagens:
- Declaração de lógica pura e inferência automática
Desvantagens:
- Dificuldade em tarefas não lógicas e performance
## Como escolher o paradigma adequado para um objeto
## Analisar as necessidades do projeto
Entender os requisitos e o escopo para determinar a abordagem mais adequada.
## Avaliar as habilidades da equipe
Considerar as competências e experiências para escolher um paradigma que melhor se alinhe com o conhecimento existente.
## Testar a viabilidade e eficiência
Realizar protótipos ou estudos de caso para avaliar a adaptabilidade e desempenho de cada paradigma no contexto do projeto
# O que é POO?
## Definição
A POO é um paradigma de programação que permite a modelagem de conceitos do mundo real, como objetos e suas interações por meio de estruturas de dados e métodos.
### Representando objetos do mundo real
#### Modelagem precisa
A POO permite a representação fiel de objetos reais, incluindo suas propriedades e comportamentos, através de classes e objetos.
#### Simulação de comportamentos
É possível simular a interação entre objetos do mundo real, como veículos, animais e dispositivos eletrônicos, facilitando a compreensão e análise de cenários complexos.
### Estruturas que fazem sentido nos programas
Além de representar objetos, os objetos também podem ser utilizados para representar estruturas de dados, como filas e pilhas. Essas estruturas são amplamente utilizadas em programação para organizar e manipular dados de forma eficiente.
### Desafios na implementação de POO
#### Abstração adequada
A identificação e criação de abstrações precisas para os objetos do mundo real podem representar um desafio significativo.
#### Complexidade crescente
À medida que os projetos crescem, a estrutura e a relação entre os objetos podem se tornar complexas e difíceis de manter
## Princípios
Na POO, os objetos são as principais entidades. Eles podem conter dados na forma de campos (atributos) e código na forma de procedimentos (métodos).
### Estado (são os atributos)
São representados por variáveis
### Operações (são os métodos)
São representados por funções. As funções modificam o estado do objeto.
### Atributos
Também chamados de membros de dados, propriedades ou campos, os atributos representam as características dos objetos pertencentes à classe. Eles armazenam dados que descrevem o estado de um objeto.
### Método
Também conhecidos como funções ou procedimentos, os métodos representam os comportamentos dos objetos. Eles são blocos de códigos que definem as ações que um objeto pode realizar ou responder. Alguns métodos comuns de colocar nas classes são aqueles que retornam o estado de um atributo.

Atributos e métodos são chamados de membros da classe ou do objeto.
### Objetos
Um objeto é uma instância de uma classe. Ele é uma entidade individual que possui características específicas e pode realizar ações ou métodos conforme definido pela classe à qual pertence.
### Classe
Uma classe é um modelo ou uma planta baixa para criar objetos. Ela define as características e comportamentos comuns a um grupo de objetos relacionados. Uma classe é como um molde a partir do qual múltiplos objetos individuais podem ser criados.
### Construtor
Um construtor é um método especial dentro de uma classe que é automaticamente invocado quando um objeto dessa classe é criado. Ele é usado para inicializar o estado interno do objeto, definir valores padrão para os atributos da classe ou executar outras operações necessárias para garantir que o objeto seja criado corretamente.
## Composição
A composição de objetos envolve a criação de objetos complexos combinando vários objetos menores. É uma forma de organizar e estruturar a funcionalidade dos objetos.
### Membros estáticos
É como se fosse uma variável global. Ela é uma variável da classe em si e não somente do objeto. Então ela modifica valores para todos os objetos da classe. Podem ser tanto atributos estáticos quando métodos estáticos.
Por exemplo, numa classe que representa cadeira. Se tivermos criando várias cadeiras e tivermos um atributo estático que conta quantas cadeiras, quando imprimirmos esse valor ele terá a quantidade de cadeira, desde que o valor seja alterado toda vez que uma cadeira é criada.
