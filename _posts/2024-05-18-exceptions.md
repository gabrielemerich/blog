---
title: Exceptions, tratar ou evitar ?
date: 2024-05-18 11:00:00
categories: [TECHNOLOGY, PROGRAMMER, EXCEPTION_HANDLER]
tags: [exceptions, programmer]
pin: true
math: true
mermaid: true
image:
  path: /assets/img/exception.png
  alt: try catch image
---

Desde quando começamos a engatinhar no mundo da programação, ou até mesmo em nossa jornada acadêmica, elas sempre estiveram ali,
principalmente quando recebiamos um StackOverflowException devido a um loop infinito ou uma recursão infinita rsrs.

Nos foi ensinado sobre a importância em manter fluxo de execução de aplicação estável, sem interrupções quando uma exceção é lançada.

A questão é, como aplicar isso da maneira correta sem afetar o desempenho do aplicativo.

Após algumas leituras, percebi que o melhor dos mundos seria codificar sem brechas para o disparo de exceções, ou seja, a existência de pré-condições antes de invocar determinada instrução, é preferível do que ter diversos blocos try/catch espalhados pelo código. Claramente as aplicações devem estar preparadas
para quando elas inevitavelmente ocorrem.

# Performance

''Por baixo dos panos'', o custo do lançamento de exceções envolve a criação de um objeto de exceção e o rastreamento de pilha (stack trace), dependendo do
o número de execuções de um determinada função, por exemplo, isso pode sair caro por ser necessário encontrar o bloco de código adequado para tratar a exceção
disparada. No .NET, por exemplo, o custo de lançar e capturar uma exceção pode ser significativamente maior do que operações normais devido à necessidade de construir o stack trace e a complexidade do mecanismo de exceções.

# Tester-Doer Pattern

Esse padrão é utilizado para membros geradores de exceção, onde primeiro testamos e só depois executamos, evitando assim problemas de desempenho
em cenários onde determinada função é chamada com frequência.

Segue o exemplo do próprio site da microsoft:

```c#
ICollection<int> numbers = ...
numbers.Add(1);
```

É sabido que o método Add gerará uma exceção caso o acesso à lista numbers for do tipo readonly, sendo assim podemos primeiro testar se a coleção permite a gravação:

```c#
ICollection<int> numbers = ...
...
//tester
if (!numbers.IsReadOnly)
{
    //doer
    numbers.Add(1);
}
```

Contudo, percebemos que é possível manter um bom design de estrutura e desempenho, no que se refere ao tratamento de exceções, desde que saibamos usa-las com eficiência, principalmente quando são executadas inúmeras vezes.

Aprofunde-se um pouco mais:

https://learn.microsoft.com/pt-br/dotnet/standard/design-guidelines/exceptions-and-performance
