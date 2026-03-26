# Aula 03: Dedução, Regras de Inferência e Lógica de Predicados

## 1. Argumentos e Validade

Um **Argumento** é um conjunto de proposições onde uma delas (conclusão) deriva das outras (premissas).
Um **Argumento** é uma sequência de proposições onde as **Premissas** devem oferecer suporte para a aceitação da **Conclusão**.

### A) Exemplo de Argumento Válido
Um argumento é válido quando é impossível que as premissas sejam verdadeiras e a conclusão seja falsa ao mesmo tempo. Um argumento é válido se, e somente se, em todas as situações onde as premissas são verdadeiras, a conclusão também é obrigatoriamente verdadeira.

* **Premissa 1:** Todo aluno de ADS sabe programar.
* **Premissa 2:** Bruna é aluna de ADS.
* **Conclusão:** Logo, Bruna sabe programar.
* **Exemplo:** Note que a conclusão "salta" das premissas de forma necessária. Se aceitamos as duas primeiras frases, não temos como negar a terceira.

### B) Exemplo de Argumento Inválido (Sofisma/Falácia)
Mesmo que as frases pareçam verdadeiras isoladamente, se a estrutura não for conexa, o argumento é inválido. É o processo de derivar a conclusão a partir das premissas usando regras lógicas.

* **Premissa 1:** Se um computador está sem bateria, ele desliga.
* **Premissa 2:** O computador de João está desligado.
* **Conclusão:** Logo, o computador de João está sem bateria.
* **Exemplo:** Este argumento é **inválido**. Por quê? Porque existem outros motivos para um computador estar desligado (ele pode estar quebrado, ou apenas fechado). A estrutura não garante a conclusão.

### C) Verdade vs. Validade
A lógica não julga se as frases são "verdades reais" do mundo, mas se a estrutura do pensamento é correta.

* **Argumento Válido com frases Falsas:**
    * **P1:** Todo gato voa. (Falso)
    * **P2:** Garfield é um gato. (Verdadeiro)
    * **C:** Logo, Garfield voa. (Falso)
* **Veredito:** O argumento é **Válido**. Embora a conclusão seja mentirosa no mundo real, ela é uma consequência lógica perfeita das premissas apresentadas.


## 2. Regras de Inferência: O Motor da Dedução

As regras de inferência são formas de argumentos válidos que servem como "atalhos" para não precisarmos fazer tabelas-verdade gigantes.

### A) Modus Ponens (Afirmação do Antecedente)

É a regra mais comum na programação (if p then q). Se a condição ocorre, o resultado é disparado.
    * Premissa 1: $p \rightarrow q$ (Se chover, a rua molha)
    * Premissa 2: $p$ (Choveu)
    * Conclusão: $\therefore q$ (Logo, a rua molhou)
    * **Exemplo Prático:**
      1. Se o usuário digitar a senha correta ($p$), então o acesso é liberado ($q$).
      2. O usuário digitou a senha correta ($p$).
      3. **Conclusão:** O acesso está liberado ($\therefore q$).

### B) Modus Tollens (Negação do Consequente)

Trabalha com a lógica reversa. Se o resultado esperado não aconteceu, a causa necessária também não ocorreu.
    * Premissa 1: $p \rightarrow q$ (Se há fogo, há fumaça)
    * Premissa 2: $\neg q$ (Não há fumaça)
    * Conclusão: $\therefore \neg p$ (Logo, não há fogo)
    * **Exemplo Prático:**
      1. Se o sensor detectar fumaça ($p$), então o alarme toca ($q$).
      2. O alarme não está tocando ($\neg q$).
      3. **Conclusão:** O sensor não detectou fumaça ($\therefore \neg p$).
         
### C) Silogismo Hipotético (Regra da Transitividade)

Permite conectar três ou mais proposições em uma sequência lógica. Muito usado em fluxogramas de sistemas.
    * Premissa 1: $p \rightarrow q$
    * Premissa 2: $q \rightarrow r$
    * Conclusão: $\therefore p \rightarrow r$
    * **Exemplo Prático:**
      1. Se o servidor cair ($p$), o site fica offline ($q$).
      2. Se o site ficar offline ($q$), a empresa perde vendas ($r$).
      3. **Conclusão:** Se o servidor cair, a empresa perde vendas ($\therefore p \rightarrow r$).

## 3. Lógica de Predicados e Quantificadores 

Até agora, tratamos as frases como blocos fechados. A **Lógica de Predicados** permite "olhar dentro" da frase, analisando sujeitos e propriedades.

### A) O que é um Predicado?
É uma afirmação sobre um sujeito ($x$). Na computação, pense no predicado como uma **função booleana** que retorna V ou F.
* **Exemplo:** $P(x)$ onde $P$ é o predicado "é par".
    * $P(2)$ é Verdadeiro.
    * $P(3)$ é Falso.

### B) Os Quantificadores
Eles definem o **alcance** da nossa afirmação dentro de um conjunto (domínio).

1.  **Quantificador Universal ($\forall$):** Significa "para todo", "para cada", "qualquer que seja".
    * **Simbologia:** $\forall x, P(x)$
    * **Exemplo:** "Todos os alunos de ADS estudam lógica". Se houver **um único** aluno que não estuda, a frase inteira torna-se Falsa.
2.  **Quantificador Existencial ($\exists$):** Significa "existe pelo menos um", "algum", "há um".
    * **Simbologia:** $\exists x, P(x)$
    * **Exemplo:** "Existe um aluno que é monitor". Basta encontrar **um único** caso para a frase ser Verdadeira.

## 4. Negação de Quantificadores (Leis de De Morgan para Predicados) 

Negar que "Todos são" não significa dizer que "Ninguém é", mas sim que "Pelo menos um não é". Negar um quantificador exige trocar o símbolo e negar o predicado. É uma ferramenta essencial para testar falhas em sistemas.

### A) Negando o "Todo" ($\forall$)
Negar que **todos** fazem algo é o mesmo que dizer que **pelo menos um** não faz.
* **Regra:** $\neg (\forall x, P(x)) \equiv \exists x, \neg P(x)$
* **Exemplo:**
    * Frase: "Todos os arquivos foram salvos."
    * Negação: "Não é verdade que todos os arquivos foram salvos" $\equiv$ "**Existe algum** arquivo que **não** foi salvo."

### B) Negando o "Existe" ($\exists$)
Negar que **existe pelo menos um** é o mesmo que dizer que **ninguém/nenhum** faz.
* **Regra:** $\neg (\exists x, P(x)) \equiv \forall x, \neg P(x)$
* **Exemplo:**
    * Frase: "Existe um bug no sistema."
    * Negação: "Não é verdade que existe um bug" $\equiv$ "**Todos** os componentes estão **sem** bug (não possuem bug)."

## 5. Exercícios

**Exercício 1: Validação de Argumento**
* **Estrutura:** Se $P \rightarrow Q$ e temos $\neg Q$, concluímos $\neg P$.
* **Resposta:** Argumento **Válido**. Trata-se do **Modus Tollens**. Se a consequência é falsa, a causa obrigatoriamente não ocorreu.

**Exercício 2: Tradução Simbólica**
* **Frase:** "Algum aluno de ADS não estuda Python".
* **Resposta:** $\exists x (A(x) \wedge \neg S(x))$
    * Onde $A(x)$ é "x é aluno de ADS" e $S(x)$ é "x estuda Python".

**Exercício 3: Conversão Binária (11000000)**
* **Cálculo:** * $(1 \cdot 2^7) + (1 \cdot 2^6) + (0 \cdot 2^5) + (0 \cdot 2^4) + (0 \cdot 2^3) + (0 \cdot 2^2) + (0 \cdot 2^1) + (0 \cdot 2^0)$
    * $128 + 64 + 0 + 0 + 0 + 0 + 0 + 0 = \mathbf{192}$.
* **Dica:** Comente que 192 é um número muito comum em endereços IP (ex: 192.168.0.1).
