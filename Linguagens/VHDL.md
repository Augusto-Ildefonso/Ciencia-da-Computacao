VHDL é uma linguagem de especificação de padrão internacional para descrever hardware usado pela industria no mundo todo. Ela permite modelar hardware das portas lógicas até o sistema. Ela fornece um mecanismo para design digital e reutilização de documentações de design.
O nome do arquivo VHDL tem quer ser o mesmo da entidade. Dentro da entidade declaramos uma arquitetura, e nela temos linhas de códigos que podem ser executadas de forma sequencial ou de forma paralela.
# Declaração da entidade
Uma declaração de entidade descreve a interface do componente. A clausula PORT indica input ou output de portas. A entidade pode ser pensada como o símbolo do componente.
~~~VHDL
ENTITY half_adder IS

	PORT(x, y, enable: IN bit;
		carry, result: OUT bit);

END half_adder;
~~~
# Declaração de arquitetura
A declaração da arquitetura descreve a operação do componente. Muitas arquiteturas podem existir dentro de uma entidade (mas o comum é ter só uma) mas somente uma está ativa por vez. A arquitetura é semelhante ao esquemático do componente.
~~~VHDL
ARCHITECTURE behavior1 of half_adder is BEGIN
	PROCESS(enable, x, y) BEGIN
	IF (enable = '1') THEN
		result <= x NOR y;
		carry <= x AND y;
	ELSE
		carry <= '0';
		result <= '0';
	END PROCESS
~~~
Poderia pensar que o process seria algo semelhante de uma função, porém o parenteses dele não é passagem de parâmetros, e sim um gatilho para quando uma das variáveis dentro dele mudar, ele executa o código.
# Processos
As tarefas são executadas sequencialmente. Tarefas sequenciais são:
- Atribuição de sinais ou variáveis
- Controle de fluxo
	- if ***condition*** then ***statements*** else ***statements*** end if;
	- for **range*** loop ***statements*** end loop;
	- while 