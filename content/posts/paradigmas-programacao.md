---
title: "Paradigmas de Programação"
date: 2022-07-14T21:49:05-03:00
draft: false
cover:
    image: "images/library-cover.jpg"
    alt: "Library"
---

Fala pessoal, beleza?  

Neste post (e nos próximos) vou comentar um pouco sobre os paradigmas de programação e suas implementações em algumas linguagens. 

Minha ideia é analisar como um determinado problema pode ser resolvido de diferentes formas por diferentes paradigmas e linguagens. 

Cada paradigma e linguagem tem suas características e isso nos ajuda a pensar de forma diferente. 

## O que é um paradigma de programação?  

Um paradigma é uma forma de se programar, onde temos um modelo a ser seguido. Cada paradigma tem seu conjunto de regras e estruturas usadas em sua implementação.  

Um paradigma pode ser melhor que outro para resolver um determinado problema.  

## Os paradigmas  

Existe um certo agrupamento de paradigmas, são eles:   

- Imperativo  
    - Estruturado;  
    - Orientado a objetos;  
- Declarativo  
    - Funcional;  
    - Lógico.  

Existem algumas outras classificações de paradigmas, mas vou me concentrar nessas.  

### Imperativo  

É o paradigma que descreve o processamento e a lógica em ações e comandos que podem ou não alterar o estado de um valor. Neste paradigma, nós falamos ao computador **como** fazer uma determinada tarefa. O nome do paradigma tem a ver com tempo verbal imperativo. São comandos com "faça", "escreva", “calcule”. 

Exemplos de linguagens: FORTRAN, COBOL, C,   

### Estrutural   

Podemos dizer que este paradigma está relacionado (ou é um subtipo) com o paradigma imperativo.  

Uma característica aqui é que este paradigma impõe sobre a estrutura de controle de execução: temos estruturas que controlam o fluxo de execução do código (os famosos `is/else`, `for`, `while` e etc.).  

Exemplos de linguagens: C, C++, Pascal, Java, PHP  

### Orientado a Objetos  

Outro paradigma relacionado ao Imperativo, o paradigma Orientado a Objetos apresenta características que nos permitem agrupar e relacionar **estado** e **comportamento**: os objetos.   

Um objeto pode ter propriedades para descrever seu estado, e funções que têm o comportamento de alterá-lo.  

Existem 3 conceitos que são bastante utilizados neste paradigma: Encapsulamento, Herança e Polimorfismo.  

Exemplos de linguagens: Smalltalk, C#, Java, C++, Python, Ruby  

### Declarativo  

É um paradigma onde temos declarações de dados e estruturas, mas não temos a declaração das instruções e comandos da máquina. É como se nós informássemos ao computador como querermos as coisas, e não como fazê-las, diferente da programação imperativa.  

Exemplos de linguagens: Prolog, Haskell, SQL  

### Funcional  

Baseado no conceito de funções matemáticas, este paradigma faz uso dessas funções e expressões para a transformação de um estado. Um conceito importante neste paradigma é o da imutabilidade.  

Ao invés de ter um procedimento que altere o estado de um determinado dado, a ideia neste paradigma é que este procedimento gera um novo estado baseado no dado original, garantindo a imutabilidade deste.  

Exemplos de linguagens: F#, Haskell, Clojure, ML  
  
### Lógico  

Consiste na ideia de se construir um conjunto de fatos e regras, e a partir destas o computador tenta encontrar uma solução.   

Exemplos de linguagens: Prolog, Datalog  

### Linguagens multiparadigma 

Uma linguagem de programação pode implementar diversos paradigmas, o que torna ela uma linguagem **multiparadigma**.  

Alguns exemplos: C#, Python, C++, Ruby, Swift, Kotlin 

## O desafio

O desafio que vou utilizar para comparar os paradigmas e as linguagens é o FizzBuzz.  

É um desafio de solução bem simples, mas que é o suficiente para podermos ver as implementações em diferentes formas.  

A tarefa é a seguinte: escrever um programa que imprima os números de 1 a N, sendo que se o número for múltiplo de 3, deve ser impresso “Fizz” no lugar do número, se for múltiplo de 5, deve ser impresso “Buzz”, se for múltiplo de 3 e 5, deve ser impresso “FizzBuzz”. Se não entrar nessas condições, então deve ser impresso o número normalmente.  

O resultado esperado é algo assim:  

```text  

1, 2, Fizz, 4, Buzz, Fizz, 7, 8, Fizz, Buzz, 11, Fizz, 13, 14, Fizzbuzz, 16, 17, Fizz, 19, Buzz, Fizz, 22, 23, Fizz, Buzz, 26, Fizz, 28, 29, Fizzbuzz, 31, 32, Fizz, 34, Buzz, Fizz, ...  

```  
___  

Nas próximas postagens, vamos ver sobre a resolução do Fizzbuzz em diferentes formas, e analisar um poucos os paradigmas e linguagens de programação.  

Até a próxima!  
