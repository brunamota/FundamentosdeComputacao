# Aula 01: Lógica Proposicional e Tomada de Decisão na Computação

## 1. Introdução à Lógica Computacional

A lógica não é apenas filosofia; é a ferramenta que estrutura linguagens formais e técnicas de programação.

* **Proposição:** Uma sentença declarativa que pode ser apenas **Verdadeira (V/1)** ou **Falsa (F/0)**.
* **Princípios Fundamentais:**
  * **Não Contradição:** Uma proposição não pode ser V e F ao mesmo tempo.
  * **Terceiro Excluído:** Ou é V ou é F, não existe "meio termo".
* Premissa: Uma proposição (ou conjunto delas) que serve como base ou fundamentação para uma conclusão.
* Conclusão: A parte final de uma inferência; a proposição que se pretende obter a partir das premissas.
* Inferência: O processo mental ou conjunto de proposições em que as premissas são apresentadas para sustentar a conclusão.
* Relação Lógica: A conexão que liga as premissas à conclusão, garantindo a validade do argumento.

* Exemplo de Argumento Lógico:
```
Premissa 1: Todo aluno de ADS estuda Python.

Premissa 2: Bruna é aluna de ADS.

Conclusão: Logo, Bruna estuda Python.
```
## 2. Operadores Lógicos na Prática

Para criar algoritmos complexos, conectamos proposições simples.

| Operação | Símbolo | Regra de Ouro | Exemplo em Código |
| --- | --- | --- | --- |
| **Conjunção (E)** | $\wedge$ | Só é verdade se **ambas** forem verdadeiras. | `if (user == "admin" && pass == "123")` |
| **Disjunção (OU)** | $\vee$ | É verdade se **pelo menos uma** for verdadeira. | `if (user == "admin" || pass == "123") |
| **Negação (NÃO)** | $\neg$ | Inverte o valor lógico. | `if (!isLogado)` |
| **Condicional** | $\rightarrow$ | "Se... então". Só é falsa se a causa for V e o efeito F. | Regras de negócio/requisitos. |

---

## 3. Workshop: Construindo Tabelas-Verdade (15 min)

O número de linhas de uma análise lógica é definido por $2^n$, onde $n$ é o número de variáveis.

### Desafio Prático: Sistema de Férias

Vamos analisar a proposição composta: $P \wedge (Q \vee \neg R)$ 

* 
**P:** Funcionário tem > 5 anos de empresa.


* 
**Q:** Usou < 5 dias de atestado.


* 
**R:** Foi promovido recentemente.



**Análise de Cenário:**

* Se o funcionário tem tempo de casa ($P=V$), mas não atende aos critérios de atestado ou promoção, o sistema retorna **Falso**.


* Este tipo de proposição que mistura V e F na saída é chamada de **Contingência**.



---

## 4. Representação de Dados: Binário e Hexa (10 min)

Na computação, o valor lógico V é 1 e F é 0.

* 
**Sistema Binário (Base 2):** A base de tudo no hardware.


* 
**Sistema Hexadecimal (Base 16):** Usado para simplificar endereços de memória e cores.



### Conversão Rápida

Para converter **Octal para Hexadecimal**, passamos obrigatoriamente pelo **Binário**:

1. Octal $\rightarrow$ Binário.


2. Binário $\rightarrow$ Hexadecimal.



---

## 5. Exercício de Fixação (Para Casa)

Dadas as variáveis $a=4, b=5$ e $c=2$:

1. Qual o valor lógico de: $(a \geq c) \wedge (b < a)$?
2. Se $(a > b) \vee (c < a)$, então $x = b + (a/c)$, senão $x = 10$. Qual o valor de $x$?

---

**Bruna, você gostaria que eu gerasse os desafios práticos de código em Python ou C para acompanhar esses exemplos de lógica?**
