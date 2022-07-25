---
title: "Programacao Estruturada"
date: 2022-07-24T19:56:45-03:00
draft: true
---

# Programação Estruturada

Fala pessoal, beleza?

Hoje vamos ver sobre o paradigma de programação estruturada, um pouco de sua história, e vamos resolver o FizzBuzz de duas maneiras diferentes para comparação.

## O Paradigma 

Este paradigma tem como características o uso de estruturas de controles de do fluxo de execução do código. São as estruturas `if/else`, `while`, `do`, `for` e qualquer outro tipo de estrutura que você conhecer.

As estruturas condicionais (`if/else`) nos permitem executar um bloco de código somente de uma condição lógica for satisfeita, ou caso o contrário também.

```go
if <condicao verdadeira> {
   //execucao de um bloco de codigo
}
else {
   //execucao de um bloco de codigo
}
```

A sintaxe vai variar de acordo com a linguagem que voce usar, mas a ideia é a mesma.

As estruturas de repetição (for, while, do, etc.) nos permitem executar um bloco de codigo repetidas vezes, até que uma condição seja alcançada para que aquele fluxo seja finalizado.

```go
while <condicao de execucao> {
   execucao de um bloco de codigo
}
```

Enquanto essa condição for verdadeira, este bloco de codigo será repetido; uma vez que a condição for falsa, o fluxo de execução dessa estrutura é interrompido.

Em seu livro Arquitetura Limpa, Robert Martin fala o seguinte: 

> “A programação estruturada impõe disciplina sobre a transferência direta do controle”

Mas o que isso quer dizer? 

Quer dizer que voce nao pode (ou pelo menos nao deve) seguir o fluxo de um código de forma aleatorio ou desordenada; isso deve ser feito através dessas estruturas de controle que as linguagens possuem, para evitar que voce tenha problemas na execução do seu código.

Já ouviu falar no GOTO? Sim, é isso que queremos evitar.

## Um pouco de história

A programação estruturada foi descoberta por Edsger Dijkstra em 1968. Ele consguiu demosntrar que o uso de saltos (`goto`) era prejudicial para a estrutura de um programa.

Imagine um programa, e uma ordem de execução do codigo, onde cada linha é execudata, seguida pela próxima, iniciando da primeira linha do seu código. Com esse comando GOTO, voce consegue fazer com que a execuçao “salte” para um determinado local do seu código, e continue a execução de lá.


Em 1968, Dijkstra publicou um artigo entitulado “Go To Statement Considered Harmful” onde ele falava dos problemas do uso da instrução GOTO, e sobre as estruturas de controle. 

Aparantemente a comunidade nao ficou feliz na epoca, o bixo pegou (imagine se existissem as redes sociais como hoje), mas no fim Dijkstra venceu e isso virou um padrão. Todas as linguagens hoje possuem essas estruturas de controle, e o uso de GoTo é desencorajado por todos.


## Golang

A lingaguem que vou utilizar para resolver o FizzBuzz é a Go (ou golangm chame como quiser).

<contar um pouco sobre go>


## FizzBuzz

Vamos ao que interessa, resolver o FizzBuzz usando o paradigma Imperativo Estrutural.

Primeiro, começamos declarando o nome do pacote e importando a biblioteca `fmt` que usaremos para escrever as informações no console.

Depois declaramos uma variável `count` que usaremos para 
facilitar o controle da execução. Vou deixar com o valor de 15, mas caso voce queira rodar o fizzbuzz com um valor diferente, basta alterar esta variável.

Em seguida, nós inserimos uma estrutura de repetição para executar um bloco de código repetidas vezes.

```go
for i := 1; i <= count; i++ {

}
```

Todo o código dentro desse par de chaves será executado 15 vezes, ao final de cada iteração, essa variável `i` é incrementada em 1 (por isto essa sintaxe `i++`).

Agora que temos nossa iteração configurada, vamos começar a validar os números.

Se o número for divisível por 3 e 5 então temos que escrever "FizzBuzz", isso tradutizo em código fica assim: 

```go
if i % 3 == 0 && i % 5 == 0 {
}
```


Se você não entendeu nada do que está escrito ali:
 - O operador `%` é responsável por retornar o resto da divisão entre dois números.
    - Ex.: 10 % 2 representa o resto da divisão de 10 por 2;
 - `&&` é o operador lógico AND, ele retorna **verdadeiro** se os dois operadores forem **verdadeiro** também.;
- Uma tradução para o portugues seria: Se o resto da divisão entre `i` e 3 é zero e e entre `i` e 5 também é zero, então execute o bloco de código.

Se a condição for vedadeira, então devemos escrever o FizzBuzz na tela:

```go
if i % 3 == 0 && i % 5 == 0 {
    fmt.Print("FizzBuzz ")
}
```
Para simplificar um pouco, ao invés de verificar se o número é multiplo de 3 e de 5, podemos verificar se ele é múmtiplo de 15,
deixando o código um pouco mais limpo, mas com o mesmo resultado

```go
if i % 15 == 0 {
    fmt.Print("FizzBuzz ")
}
```

A ideia segue a mesma, agora com as outras validações, se o número for múltiplo de 5, devemos escrever `Buzz`:

```go
if i % 5 == 0 {
    fmt.Print("Buzz ")
}
```

Se o número for múltiplo de 3, então escrevemos `Fizz`:

```go
if i % 3 == 0 {
    fmt.Print("Fizz ")
}
```

Caso o contrário, nós escrevemos o número na tela.
Juntando tudo, nós temos o seguinte código:

```go
func main() {
	count := 15

	for i := 1; i <= count; i++ {
		if i % 15 == 0 {
			fmt.Print("FizzBuzz ")
		} else if i % 5 == 0 {
			fmt.Print("Buzz ")
		} else if i % 3 == 0 {
			fmt.Print("Fizz ")
		} else {
			fmt.Printf("%d ", i)
		}
	}
}
```

O resultado: 

```text
1 2 Fizz 4 Buzz Fizz 7 8 Fizz Buzz 11 Fizz 13 14 FizzBuzz
```

Simples, correto?
Para mim é algo trivial, já que comecei na programação com lingugens imperativas estruturadas, então isso parece muito natural, como poderia existir algo sem uma estruturas de repetição?

## Uma resolução não estruturada

Bem, decidi então fazer a resolução do mesmo problema, porém sem usar estruturas de repetição, parar ter uma ideia de como seria programar sem esse tipo de restrição que o paradigma nos impõe.

Fiz o mesmo exemplo em Batch, porém usando “saltos” com as instruções GOTO, e ficou assim: 

```batch
@echo off
SET /A max = 15
SET /A count = 1

GOTO :handling

:increase_counter
SET /A count = %count% + 1
if %count% GTR %max% GOTO :EOF

:handling

:handle_15
SET /a m = %count% %% 15
if %m% == 0 (
    echo FizzBuzz
    GOTO :increase_counter
)

:handle_3
SET /a m = %count% %% 3
if %m% == 0 (
    echo Fizz
    GOTO :increase_counter
)

:handle_5
SET /a m = %count% %% 5
if %m% == 0 (
    echo Buzz
    GOTO :increase_counter
)

:handle_number
echo %count%
GOTO :increase_counter

```

Repare na diferença do código, como fica mais complexo usando os saltos, e muito mais sucetivel ao erro. Nós consgeguimos criar identificaçõe de áreas no código, como o `:increase_counter`, conseguimos mover a execução para esta área a qualquer momento, usando o `GOTO :increase_counter`

A estrutura de repetição faz com que nao seja preciso usar esses saltos, e nos dá uma abstração para realizar essa tarefa: muito mais prático usar um laço `for` do que `goto` para controlar o fluxo.

## Conclusão

TODO