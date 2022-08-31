---
title: "Programação Funcional"
date: 2022-08-19T22:59:44-03:00
draft: false
---

Fala pessoal, beleza? 

Hoje vamos ver sobre o paradigma de programação funcional, um pouco de sua história e vamos resolver o FizzBuzz usando a linguagem Clojure.

## O Paradigma

O paradigma funcional tem como base o uso de funções para a realização das operações. Quando falamos em função, é literalmente uma função matemática (aquelas funções que você deve ter visto na escola)

Considere a função:

```
f(x) = x * 2
```

avaliar este texto 

Essa função recebe um parâmetro (X) e retorna o dobro do valor (x * 2). Esta função não faz nada além de calcular o dobro do valor (para qualquer valor informado, sempre será calculado o dobro) e nunca altera o valor de X - ele sempre vai ser X independente de qualquer coisa. Este conceito de função é aplicado para qualquer tipo de processamento neste paradigma.

Uma função pode ser categorizada entre **pura** e **impura**.
- As funções puras são aquelas que sempre retornam o mesmo valor, de acordo com os parâmetros passados, e não possuem efeitos colaterais (um efeito colateral seria uma alteração de uma variável, chamado a um banco de dados, interação com o teclado ou qualquer coisa do tipo); daí o nome “pura”.
- As funções impuras são o contrário, elas podem ter efeitos colaterais e resultado da função pode variar a cada execução de um determinado parâmetro de entrada.


**Imutabilidade**

Uma característica importante neste paradigma é a imutabilidade: uma vez que um dado é criado, ele não é modificado por estas funções, mas é gerado um novo valor com base na informação original. Isto te dá a garantia de que você não vai perder o valor original de sua variável.

Como no exemplo anterior `f(x) = x * 2`, a variável `x` terá sempre o mesmo valor; esta função não modifica o valor de `x`, mas cria um novo valor, que é o resultado de `x * 2`.

Você pode achar que a imutabilidade não faz sentido ou não seja necessária para seu código, mas em muitos casos, ter a garantia de que sua informação não será modificada é extremamente importante.

**Composição**

Outra característica bastante utilizada é a composição. Isso permite com que você possa agrupar funções que irão processar algo em sequência - o resultado de uma função é passado para outra, e assim é feito em sequência. Pense em um fluxo onde você pode adicionar ou remover algum processamento de forma muito fácil, além do fato de que você pode testar essas funções separadamente de forma prática.

```js
// declarando as funções de forma separada
add1 = x => x + 1;
sub1 = x => x - 1;
div2 = x => x / 2
mult3 = x => x * 3

// poderíamos chamar essas funções de forma encadeada assim
result = mult3(div2(sub1(add1(6))))
result // 9

/*
 * ou em muitos casos em linguagens funcionais, 
 * poderíamos mesclar e compor estas funções 
 * de uma forma parecida com esta
*/
result = 6 > add1 > sub1 > div2 > mult3
result // 9
```

## Um pouco de história

A programação funcional é baseada em um sistema criado por um matemático chamado Alonzo Church.

Em 1936, Church publicou um artigo introduzindo o Cálculo Lambda (ou Cálculo-λ). Este é um sistema formal para expressar modelos computacionais através de funções; em tese é possível expressar qualquer operação utilizando este sistema.

Uma função que recebe um parâmetro e retorna o seu valor mais 1 pode ser representada da seguinte forma:

```math
λx.x+1
```

As linguagens de programação funcional tem como base o sistema do cálculo lambda, daí temos os conceitos e representações parecidos.

Church foi orientador de doutorado de Alan Turing. Os dois têm trabalhos semelhantes, onde as mesmas tarefas computacionais que podem ser representadas no Cálculo Lambda podem ser representadas em uma Máquina de Turing.

## Lisp e Clojure

Lisp é uma linguagem criada baseada no Cálculo Lambda. Lisp foi criada em 1958 por John McCarthy; seu nome vem do termo “**LIS**t **P**rocessor”

Hoje quando falamos em Lisp nos referimos à uma família de linguagens, família que possui vários “dialetos” como Racket, Common Lisp, Scheme e Clojure, que vamos utilizar hoje. 

Logo, se você conhecer alguma linguagem que “é da família Lisp”, essa linguagem provavelmente terá uma sintaxe muito parecida com todas as da família.

É uma linguagem dinâmica e multi paradigma que possui uma sintaxe, digamos, peculiar (ao menos para quem nunca teve contato), fazendo uso de recursos e padrões diferentes dos que estamos acostumados nas linguagens de programação mais comuns hoje em dia.

Um exemplo é o uso da notação prefixa (ou notação polonesa) onde o operador vem antes dos operandos. Uma operação como `2 + 2` seria representada dessa forma: `+ 2 2`, isso vale para as outras operações, como a de comparação `> 2 1`.

Outra característica é o uso de parênteses na representação das expressões (S-expressions) e nas chamadas de funções. Para chamar uma função `callFunc` em uma linguagem baseada em C por exemplo, basta chamar `callFunc()` desta forma; em Lisp a sintaxe ficaria assim: `(callfunc)`, com o nome da função entre parêntesis.

### Clojure

Clojure é uma linguagem de programação (um dialeto de Lisp) criada em 2007 por Rich Hickey. É uma linguagem dinâmica e roda em cima da JVM (Java Virtual Machine).

Por ser um dialeto de Lisp, apresenta as mesmas características citadas acima. Para exemplo, uma função como: 

```js
function addNumbers(x, y) {
	return x + y;
}
addNumbers(2, 2); // 4
```

Ficaria assim em Clojure:

```clj
(defn addNumbers [x y]
	(+ x y))

(addNumbers 2 2) ;; 4
```


Aquele exemplo que comentei sobre a composição, onde podemos utilizar funções de forma encadeada? Em Clojure, podemos ter algo assim:

```clj
(defn add1 [n] (+ n 1))
(defn sub1 [n] (- n 1))
(defn div2 [n] (/ n 2))
(defn mult3 [n] (* n 3))

(-> 6 add1 sub1 div2 mult3) ;; 4

```
Sim, no começo parece estranho, mas você se acostuma.

## Resolvendo o FizzBuzz

Vamos ao que interessa, resolver o FizzBuzz usando o paradigma declarativo funcional.

Primeiro, vamos criar uma função `mapNumber` que receba um número  e converta para o resultado esperado: Fizz, Buzz, FizzBuzz ou o próprio número.

```clj
;; isso é um comentário em clojure

(defn mapNumber ;; nome do método
  [i] ;; declaração do parâmetro
	;; corpo da função aqui
)
```

A seguir, nós usamos uma função chamada `cond` para testar todas as possibilidades de divisão. Aqui nós também temos o operador `mod` para ajudar a verificar se um número é divisível por outro.

Para verificar se um número é igual a 0, por exemplo, nós usamos a operação `(= i 0)`; para encontrar o resto da divisão de um número por 3, usamos a operação `(mod i 3)`.

Em uma linguagem com a notação infixa (a que você provavelmente está acostumado), essa expressão ficaria parecida com isso:

```
i mod 3 == 0
```
Em Clojure, nós temos
```clj
(= 0 (mod i 3))
```

Tendo essa expressão em mente, vamos usá-las para montar nossa expressão de validação usando `cond`. Basta adicionar essas condições em uma sequência, junto com o valor desejado de retorno caso aquela expressão seja satisfeita. Se nada for encontrado, então retornamos o próprio número.

```clj
(cond
    (= 0 (mod i 15)) "FizzBuzz"
    (= 0 (mod i 5)) "Buzz"
    (= 0 (mod i 3)) "Fizz"
    :else (str i))
```

Agora, basta adicionar essa expressão em nossa função mapNumber e temos nosso mapeamento completo. Para validar a função, basta chamá-la passando algum número e verificar o retorno.

```clj
(defn mapNumber
  [i]
  (cond
    (= 0 (mod i 15)) "FizzBuzz"
    (= 0 (mod i 5)) "Buzz"
    (= 0 (mod i 3)) "Fizz"
    :else (str i)))
 
(mapNumber 1)   ;; 1
(mapNumber 3)   ;; Fizz
(mapNumber 5)   ;; Buzz
(mapNumber 15)  ;; FizzBuzz
```

Agora precisamos gerar uma lista de 1 até n numeros e gerar nosso fizzbuzz.

Nós vamos usar a função `range` para gerar uma coleção de número de 1 até `n` e então usar nossa função `mapNumber` para mapear esses resultados. Essa lógica ficará em uma função chamada `fizzbuzz`.

```clj
(defn fizzbuzz [n]
  (range 1 n))

(fizzbuzz 10) ;; (1 2 3 4 5 6 7 8 9)
```

Se chamarmos essa função, ela retornará uma coleção com os números gerados.

Vamos aplicar uma função `map` sobre esses números para podermos transformar esses valores.

```clj
(map funcao-de-mapeamento (range 1 n))
```

Qualquer função que passarmos nesse `map` será chamada para todos os itens da coleção. Vamos usar nossa função `mapNumber`.

```clj
(map mapNumber (range 1 n))
```

Nossa função fizzbuzz ficaria assim

```clj
(defn fizzbuzz [n]
  (map mapNumber (range 1 n)))
```

Pronto, se chamar a função passando algum número, teremos nosso fizzbuzz.

```clj
(fizzbuzz 16) 
;; ("1" "2" "Fizz" "4" "Buzz" "Fizz" "7" "8" "Fizz" "Buzz" "11" "Fizz" "13" "14" "FizzBuzz")
```

Uma melhoria que podemos fazer é criar um comportamento diferente no método, de acordo com o número de argumentos passados. Se recebermos o argumento n, vamos chamar a função `map` normalmente; se não recebermos um argumento `n`, então vamos chamar a função fizzbuzz recursivamente, passando o argumento `n` com um valor padrão.

```clj 
(defn fizzbuzz

  ([n] 
   (map mapNumber (range 1 n)))

  ([]
   (fizzbuzz 10))) 
```

O código final fica assim:

``` clj
(defn mapNumber
  [i]
  (cond
    (= 0 (mod i 15)) "FizzBuzz"
    (= 0 (mod i 5)) "Buzz"
    (= 0 (mod i 3)) "Fizz"
    :else (str i)))

(defn fizzbuzz

  ([n] 
   (map mapNumber (range 1 n)))

  ([]
   (fizzbuzz 10))) 
```

Repare como ficou o código e como ele fica diferente de uma linguagem imperativa. A sensação que eu tenho é que estou escrevendo uma receita de como eu quero o resultado do meu código, e não como o computador deve excecutar as instruções.

## Conclusão

Vimos como o paradigma funcional se difere do imperativo, tanto no estilo de programação, quanto em suas características. Diferente de um paradigma imperativo, aqui nós não temos instruções de execução como `for` ou `if/else`, mas declarações de funcões e mapeamento de dados. O resultado é o meso, mas conseguims atingi-lo de formas diferentes. 

Também conhecemos uma linguagem diferente do que provavelmente estamos acostumados, com características peculiares. Acredito que vale a pena dar uma atenção para uma lingaguem da família Lisp.

Por fim, implementamos o FizzBuzz usando uma lingaugem declarativa funcional.

Até a próxima!