--- 
title: "Programação Estruturada" 
date: 2022-07-24T19:56:45-03:00 
draft: false 
--- 

Fala pessoal, beleza? 

Hoje vamos ver sobre o paradigma de programação estruturada, um pouco de sua história e vamos resolver o FizzBuzz de duas maneiras diferentes para comparação. 

## O Paradigma  

Este paradigma tem como características o uso de estruturas de controles do fluxo de execução do código. São as estruturas `if/else`, `while`, `do`, `for` e qualquer outro tipo de estrutura que você conhecer. 

As estruturas condicionais (`if/else`) nos permitem executar um bloco de código somente se uma condição lógica for satisfeita, ou caso o contrário também. 

```cs 
if (<condição>) { 
   //execução de um bloco de código 
} 
else { 
   //execução de um bloco de código 
} 
``` 
A sintaxe pode variar de acordo com a linguagem que você usar, mas a ideia é a mesma. 

As estruturas de repetição (`for`, `while`, `do`, etc.) nos permitem executar um bloco de código repetidas vezes, até que uma condição seja alcançada para que aquele fluxo seja finalizado. 

```cs
while (<condição>) { 
   //execução de um bloco de código 
} 
``` 
Enquanto essa condição for verdadeira, este bloco de código será repetido; uma vez que a condição for falsa, o fluxo de execução dessa estrutura é interrompido. 

Em seu livro Arquitetura Limpa, Robert Martin fala o seguinte:  

> “A programação estruturada impõe disciplina sobre a transferência direta do controle” 

Mas o que isso quer dizer?  
Quer dizer que você não pode (ou pelo menos não deve) seguir o fluxo de um código de forma aleatória ou desordenada; isso deve ser feito através dessas estruturas de controle que as linguagens possuem, para evitar que você tenha problemas na execução do seu código. 

Já ouviu falar no GOTO? Sim, é isso que queremos evitar. 
 

## Um pouco de história 

A programação estruturada foi descoberta por Edsger Dijkstra em 1968. Ele conseguiu demonstrar que o uso de saltos (`goto`) é prejudicial para a estrutura de um programa. 

Imagine um programa e uma ordem de execução do código, onde cada linha é executada, seguida pela próxima, iniciando da primeira linha do seu código. Com esse comando GOTO, você consegue fazer com que a execução “salte” para um determinado local do seu código e continue de lá. 

Em 1968, Dijkstra publicou um artigo intitulado “Go To Statement Considered Harmful” onde ele falava dos problemas do uso da instrução GOTO, e sobre as estruturas de controle.  

Aparentemente a comunidade não ficou feliz na época, o bicho pegou (imagine se existissem as redes sociais como hoje), mas no fim Dijkstra venceu e isso virou um padrão. Todas as linguagens hoje possuem essas estruturas de controle, e o uso de GoTo é desencorajado por todos. 
 

## Golang 

A linguagem que vou utilizar para resolver o FizzBuzz é a Go (ou golang, como também é conhecida). 

Go foi criada em 2007 por Robert Griesemer, Rob Pike e Ken Thompson (sim, o mesmo cara da linguagem C e do Unix) dentro do Google; seu objetivo é ser expressiva, eficiente e eficaz para escrever programas confiáveis e robustos. 

Uma de suas inspirações é a linguagem C, onde herdou a sintaxe das expressões, passagem de parâmetro por valor, ponteiros, entre outras coisas. 

É uma linguagem poderosa, simples e fácil de aprender. 


## FizzBuzz 

Vamos ao que interessa, resolver o FizzBuzz usando o paradigma Imperativo Estrutural. 

Primeiro, começamos declarando o nome do pacote e importando a biblioteca `fmt` que usaremos para escrever as informações no console. 
```go
package main

import "fmt"

func main() {

}
```

Depois declaramos uma variável `count` que usaremos para  facilitar o controle da execução. Vou deixar com o valor de 15, mas caso você queira rodar o fizzbuzz com um valor diferente, basta alterar esta variável. 

Em seguida, nós inserimos uma estrutura de repetição para executar um bloco de código repetidas vezes. 

```go 
for i := 1; i <= count; i++ { 
} 
``` 

Todo o código dentro desse par de chaves será executado 15 vezes, ao final de cada iteração, essa variável `i` é incrementada em 1 (por isto essa sintaxe `i++`). 

Agora que temos nossa iteração configurada, vamos começar a validar os números. 

Se o número for divisível por 3 e 5 então temos que escrever "FizzBuzz", isso traduzido em código fica assim:  

```go 
if i % 3 == 0 && i % 5 == 0 { 
} 
``` 

Se você não entendeu nada do que está escrito ali: 
 - O operador `%` é responsável por retornar o resto da divisão entre dois números. 
    - Ex.: `10 % 2` representa o resto da divisão de 10 por 2;
 - `&&` é o operador lógico AND, ele retorna **verdadeiro** se os dois operadores forem **verdadeiro** também.; 
- Uma tradução para o português seria: Se o resto da divisão entre `i` e 3 é zero e entre `i` e 5 também é zero, então execute o bloco de código. 

Se a condição for verdadeira, então devemos escrever o FizzBuzz na tela: 

```go 
if i % 3 == 0 && i % 5 == 0 { 
    fmt.Print("FizzBuzz ") 
} 
``` 

Para simplificar um pouco, ao invés de verificar se o número é múltiplo de 3 e de 5, podemos verificar se ele é múltiplo de 15, 
deixando o código um pouco mais limpo, mas com o mesmo resultado.

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
package main

import "fmt"

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

Para mim é algo trivial, já que comecei na programação com linguagens imperativas estruturadas, então isso parece muito natural, como poderia existir algo sem uma estrutura de repetição? 


## Uma resolução não estruturada 

Bem, decidi então fazer a resolução do mesmo problema, porém sem usar estruturas de repetição, parar ter uma ideia de como seria programar sem esse tipo de restrição que o paradigma nos impõe. 

Fiz o mesmo exemplo em Batch, porém usando “saltos” com as instruções GOTO, e ficou assim:  

```bat 
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

Repare na diferença do código, como fica mais complexo usando os saltos, e muito mais suscetível ao erro. Nós conseguimos criar identificações de áreas no código, como o `:increase_counter`, conseguimos mover a execução para esta área a qualquer momento, usando o `GOTO :increase_counter`. 

A estrutura de repetição faz com que não seja preciso usar esses saltos, e nos dá uma abstração para realizar essa tarefa: muito mais prático usar um laço `for` do que `goto` para controlar o fluxo. 


## Conclusão 

Vimos como o paradigma estrutural nos restringe quanto aos saltos no código, e como isso é benéfico para o desenvolvimento de software. 

Foi possível ter uma noção da evolução das linguagens com o tempo, e como essa evolução afeta a experiência de programação.

Resolvemos o FizzBuzz usando a programação imperativa estruturada, agora temos uma base para comparar com os próximos paradigmas.

Até a próxima!

## Referências 

- Arquitetura Limpa - Robert C. Martin 
- A Linguagem de Programação Go - Alan A. A. Donovan, Brian W. Kernighan 

 