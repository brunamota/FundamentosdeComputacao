# Aula 01: Lógica Proposicional e Tomada de Decisão na Computação

## 1. Introdução à Lógica Computacional

A lógica não é apenas filosofia; é a ferramenta que estrutura linguagens formais e técnicas de programação.

* **Proposição:** Uma sentença declarativa que pode ser apenas **Verdadeira (V/1)** ou **Falsa (F/0)**.
* **Princípios Fundamentais:**
  * **Não Contradição:** Uma proposição não pode ser V e F ao mesmo tempo.
  * **Terceiro Excluído:** Ou é V ou é F, não existe "meio termo".
* **Premissa:** Uma proposição (ou conjunto delas) que serve como base ou fundamentação para uma conclusão.
* **Conclusão:** A parte final de uma inferência; a proposição que se pretende obter a partir das premissas.
* **Inferência:** O processo mental ou conjunto de proposições em que as premissas são apresentadas para sustentar a conclusão.
* **Relação Lógica:** A conexão que liga as premissas à conclusão, garantindo a validade do argumento.
* **Classificação de Proposições Compostas:**
 * **Tautologia:** Quando o resultado final é sempre Verdadeiro, independentemente dos valores das proposições simples.
 * **Contradição:** Quando o resultado final é sempre Falso.
 * **Contingência (ou Indeterminação):** Quando o valor lógico final apresenta uma mistura de Verdadeiros (V) e Falsos (F). O resultado depende das circunstâncias reais das premissas.

* Exemplo de Argumento Lógico:
```
Premissa 1: Todo aluno de ADS estuda Java.

Premissa 2: João é aluno de ADS.

Conclusão: Logo, João estuda Python.
```

## 2. Operadores Lógicos e Conectivos

Na programação, utilizamos conectores para unir proposições simples e formar decisões complexas. Abaixo, comparamos a simbologia lógica com as linguagens que eles verão no curso:

| Operação | Símbolo | Python | Java | Regra de Ouro |
| --- | --- | --- | --- | --- |
| **Conjunção (E)** | $\wedge$ | `and` | `&&` | Só é `True` se **todas** as partes forem verdadeiras.|
| **Disjunção (OU)** | $\vee$ | `or` | `||` | É `True` se **pelo menos uma** parte for verdadeira.|
| **Negação (NÃO)** | $\neg$ | `not` | `!` | Inverte o valor lógico: o que é V vira F.|
| **Condicional** | $\rightarrow$ | `if` | `if` | "Se p, então q". Formaliza a ideia de causa e consequência.|

Na computação, o valor lógico V é 1 e F é 0.

### Exemplos de Aplicação

Para fixar a **relação lógica** entre premissas e conclusão, veja estes exemplos fora da sintaxe de tabela:

#### A) O Operador de Conjunção (`and` / `&&`)

Só é verdadeira se **ambas** as proposições forem verdadeiras.

| $p$ | $q$ | $p \wedge q$ |
| --- | --- | --- |
| V | V | **V** |
| V | F | F |
| F | V | F |
| F | F | F |

Imagine um sistema de login. Para o acesso ser concedido (conclusão), duas premissas precisam ser verdadeiras simultaneamente:

* **Premissa 1:** O usuário existe no banco de dados.
* **Premissa 2:** A senha digitada está correta.
* **Relação Lógica:** Se `usuario_vaildo && senha_correta`, o acesso é liberado.


#### B) O Operador de Disjunção (`or` / `||`)

Só é falsa se **ambas** forem falsas.

| $p$ | $q$ | $p \vee q$ |
| --- | --- | --- |
| V | V | V |
| V | F | V |
| F | V | V |
| F | F | **F** |

Um sistema de e-commerce que oferece frete grátis:

* **Premissa 1:** O valor da compra é maior que R$ 200,00.
* **Premissa 2:** O cliente possui um cupom de "FRETE_GRATIS".
* **Relação Lógica:** Basta que **uma** das premissas seja verdadeira para a conclusão (frete zero) ser aplicada.

#### C) O Operador de Negação (`not` / `!`)

Inverte o valor lógico original.

| $p$ | $\neg p$ |
| --- | --- |
| V | F |
| F | V |


Geralmente usado para verificar estados contrários, como em sensores ou travas:

* **Proposição:** "A porta está trancada".
* **Aplicação:** Se `!porta_trancada`, o sistema deve disparar um alerta.

## 3.Construindo Tabelas-Verdade

O número de linhas de uma análise lógica é definido por $2^n$, onde $n$ é o número de variáveis.

### Desafio Prático: Sistema de Férias

Vamos analisar a proposição composta: $P \wedge (Q \vee \neg R)$ 

* **P:** Funcionário tem > 5 anos de empresa.
* **Q:** Usou < 5 dias de atestado.
* **R:** Foi promovido recentemente.

Como temos 3 variáveis, a tabela possui $2^3 = 8$ linhas.

| $P$ | $Q$ | $R$ | $\neg R$ | $(Q \vee \neg R)$ | $P \wedge (Q \vee \neg R)$ | Resultado |
| --- | --- | --- | --- | --- | --- | --- |
| V | V | V | F | V | **V** | Aprovado |
| V | V | F | V | V | **V** | Aprovado |
| V | F | V | F | F | **F** | Negado |
| V | F | F | V | V | **V** | Aprovado |
| F | V | V | F | V | **F** | Negado |
| F | V | F | V | V | **F** | Negado |
| F | F | V | F | F | **F** | Negado |
| F | F | F | V | V | **F** | Negado |

> 
> **Nota:** Como o resultado final possui tanto **V** quanto **F**, classificamos esta proposição como uma **Contingência**.
> Ouseja, no sistema de férias, se o resultado é uma contingência, significa que o software precisa avaliar os dados de cada funcionário individualmente para decidir, pois a regra não é sempre verdadeira nem sempre falsa.
> 

**Análise de Cenário:**

* Se o funcionário tem tempo de casa ($P=V$), mas não atende aos critérios de atestado ou promoção, o sistema retorna **Falso**.

* Este tipo de proposição que mistura V e F na saída é chamada de **Contingência**.

### Conversão Rápida

Para converter **Octal para Hexadecimal**, passamos obrigatoriamente pelo **Binário**:

1. Octal $\rightarrow$ Binário.
2. Binário $\rightarrow$ Hexadecimal.

## 4. Exercício de Fixação

Dadas as variáveis $a=4, b=5$ e $c=2$:

1. Qual o valor lógico de: $(a \geq c) \wedge (b < a)$?

* **Premissa 1:** $(4 \geq 2)$ é **Verdadeiro**.
* **Premissa 2:** $(5 < 4)$ é **Falso**.
* **Conclusão:** $V \wedge F =$ **Falso**.

2. Se $(a > b) \vee (c < a)$, então $x = b + (a/c)$, senão $x = 10$. Qual o valor de $x$?

* **Parte 1:** $(4 > 5)$ é **Falso**.
* **Parte 2:** $(2 < 4)$ é **Verdadeiro**.
* **Relação Lógica:** $F \vee V =$ **Verdadeiro**.
* **Resultado:** Como a condição é verdadeira, $x = b + (a/c) \rightarrow 5 + (4/2) = \mathbf{7}$.
