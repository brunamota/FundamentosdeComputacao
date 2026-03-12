# Aula 02: Relações Lógicas e Álgebra de Proposições

## 1. Do Pensamento à Estrutura Lógica

Para que um conjunto de frases se torne um algoritmo confiável, precisamos entender a dinâmica entre elas através de conceitos fundamentais:

* **Proposição:** Enunciado declarativo que assume valor **Verdadeiro (V/1)** ou **Falso (F/0)**.
* **Premissa:** Proposição dada como fundamentação ou evidência para uma conclusão.
* **Conclusão:** A parte final de uma inferência; o que se pretende obter das premissas.
* **Inferência:** O processo mental ou salto lógico que conecta as premissas à conclusão.
* **Relação Lógica:** A conexão que garante que o pensamento seja coerente e livre de ambiguidades.


### Classificação das Proposições Compostas

* **Tautologia:** Proposição sempre verdadeira, independente dos valores das variáveis (ex: $p \vee \neg p$).
* **Contradição:** Proposição sempre falsa (ex: $p \wedge \neg p$).
* **Contingência:** Quando o resultado final na tabela-verdade varia entre V e F (ex: pedidos de férias em uma empresa).


## 2. Implicação Lógica ($\Rightarrow$) (10 min)

Dizemos que uma proposição $p$ implica $q$ quando o condicional $p \rightarrow q$ é uma **tautologia**.

* **Sentido Prático:** É uma "via de mão única". Se a premissa acontece, a conclusão é obrigatória.
* **Regra de Ouro:** O condicional só é falso se tivermos o antecedente Verdadeiro e o consequente Falso (**V $\rightarrow$ F**).

| $p$ | $q$ | $p \rightarrow q$ |
| --- | --- | --- |
| V | V | V |
| V | F | **F** |
| F | V | V |
| F | F | V |

Veja os quatro cenários possíveis:

1. **V $\rightarrow$ V = Verdadeiro:** "Se hoje é segunda-feira, então amanhã é terça-feira". (Causa e efeito ocorrem).
2. **V $\rightarrow$ F = Falso:** "Se hoje é segunda-feira, então amanhã é domingo". (A única falha da regra).
3. **F $\rightarrow$ V = Verdadeiro:** "Se eu for eleito (F), os impostos diminuirão (V)". (A promessa não foi quebrada, pois a condição de ser eleito não ocorreu).
4. **F $\rightarrow$ F = Verdadeiro:** "Se eu for eleito (F), os impostos NÃO diminuirão (F)". (Sem expectativas, a lógica permanece íntegra).

## 3. Equivalência Lógica ($\equiv$ ou $\Leftrightarrow$)

Duas proposições são equivalentes quando possuem **tabelas-verdade idênticas**.

### Propriedades e Álgebra de Proposições

Essas regras permitem simplificar códigos complexos sem alterar o resultado final:

#### **A) Dupla Negação ($\neg(\neg p) \equiv p$)**

A negação da negação de uma proposição é equivalente à própria proposição original.

* **Exemplo:** "Não é verdade que Marcos não é japonês" é o mesmo que dizer "Marcos é japonês".

**Tabela-Verdade:**
| $p$ | $\neg p$ | $\neg(\neg p)$ |
| :---: | :---: | :---: |
| V | F | **V** |
| F | V | **F** |


#### **B) Leis de De Morgan**
Estas leis mostram como negar conjunções ("e") e disjunções ("ou").
**1ª Lei: Negação da Conjunção ($\neg(p \wedge q) \equiv \neg p \vee \neg q$)**
* **Exemplo:** "Não é verdade que Miguel tem um celular e um laptop" equivale a "Miguel não tem um celular **ou** não tem um laptop".

**Tabela-Verdade:**
| $p$ | $q$ | $p \wedge q$ | $\neg(p \wedge q)$ | $\neg p$ | $\neg q$ | $\neg p \vee \neg q$ |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| V | V | V | **F** | F | F | **F** |
| V | F | F | **V** | F | V | **V** |
| F | V | F | **V** | V | F | **V** |
| F | F | F | **V** | V | V | **V** |

**2ª Lei: Negação da Disjunção ($\neg(p \vee q) \equiv \neg p \wedge \neg q$)**
* **Exemplo:** "Não é verdade que Rodrigo vai ao concerto ou Carlos vai ao concerto" equivale a "Rodrigo não vai ao concerto **e** Carlos não vai ao concerto".

**Tabela-Verdade:**
| $p$ | $q$ | $p \vee q$ | $\neg(p \vee q)$ | $\neg p$ | $\neg q$ | $\neg p \wedge \neg q$ |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| V | V | V | **F** | F | F | **F** |
| V | F | V | **F** | F | V | **F** |
| F | V | V | **F** | V | F | **F** |
| F | F | F | **V** | V | V | **V** |


#### **C) Contrapositiva ($p \rightarrow q \equiv \neg q \rightarrow \neg p$)**

Uma condicional é logicamente equivalente à sua contrapositiva, onde negamos e invertemos o antecedente e o consequente.

* **Exemplo:** "Se Gustavo tem CRC, então é profissional da contabilidade" equivale a "Se Gustavo **não é** profissional da contabilidade, então **não tem** CRC".

**Tabela-Verdade:**
| $p$ | $q$ | $p \rightarrow q$ | $\neg q$ | $\neg p$ | $\neg q \rightarrow \neg p$ |
| :---: | :---: | :---: | :---: | :---: | :---: |
| V | V | **V** | F | F | **V** |
| V | F | **F** | V | F | **F** |
| F | V | **V** | F | V | **V** |
| F | F | **V** | V | V | **V** |

## 4. Ordem de Precedência

Para simplificar fórmulas e reduzir a necessidade de parênteses no código, seguimos a convenção:

1. **Parênteses:** Dos mais internos para os externos.
2. **Negação:** ($\neg$, `~`, `not`, `!`).
3. **Conjunção ($\wedge$) e Disjunção ($\vee$):** (`and`/`&&` e `or`/`||`).
4. **Condicional ($\rightarrow$):** (`if`).
5. **Bicondicional ($\leftrightarrow$):** (`==`).

## 5. Prática

Vamos aplicar os conceitos para simplificar verificações de sistemas.
Utilize os valores: $a=4, b=5$ e $c=2$.

1. **Avaliação de Proposição:** Determine o valor lógico de $(a \geq c) \wedge (b < a)$.

* **Passo 1:** Avaliar $a \geq c \rightarrow 4 \geq 2$. Resultado: **Verdadeiro (V)**.
* **Passo 2:** Avaliar $b < a \rightarrow 5 < 4$. Resultado: **Falso (F)**.
* **Passo 3:** Aplicar a conjunção ($\wedge$): $V \wedge F$.
* **Resposta:** O valor lógico resultante é **Falso (F)**.

2. **Raciocínio Condicional:** Se $(a > b)$ ou $(c < a)$, então $x = b + (a/c)$. Qual o valor de $x$?
* $(4 > 5)$ é F; $(2 < 4)$ é V.

* **Análise da condição:**
* $(a > b) \rightarrow (4 > 5)$ é **Falso (F)**.
* $(c < a) \rightarrow (2 < 4)$ é **Verdadeiro (V)**.
* Falsa ou Verdadeira ($F \vee V$) resulta em **Verdadeiro (V)**.

3. **Simplificação (De Morgan):** Refatore a negação da frase: "A prova foi fácil e Paulo joga futebol".
* $\neg(fácil \wedge joga) \equiv \neg fácil \vee \neg joga$ .

* **Definição das proposições:**
* $p$: "A prova foi fácil".
* $q$: "Paulo joga futebol".
* **Frase original:** $(p \wedge q)$.
* **Negação da frase:** $\neg(p \wedge q)$.
* **Aplicação de De Morgan:** $\neg p \vee \neg q$.
* **Resposta:** "A prova **não** foi fácil **ou** Paulo **não** joga futebol".
