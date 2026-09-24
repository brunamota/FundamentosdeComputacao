# Aula 03: Dedução, Regras de Inferência e Lógica de Predicados

## 1. Argumentos e Validade

Um **Argumento** é uma sequência de proposições em que as **Premissas** devem oferecer suporte para a aceitação da **Conclusão**.

### Aplicação no Dia a Dia

* **Debug de Sistemas:** Quando um sistema falha, o programador analisa as premissas (logs, estados de variáveis) para deduzir onde a validade do processo foi quebrada.
* **Segurança da Informação:** Auditorias de segurança usam argumentos dedutivos para provar que, se certas premissas de acesso forem atendidas, o sistema está ou não vulnerável.

### A) Argumento Válido
Um argumento é válido se, e somente se, em todas as situações em que as premissas são verdadeiras, a conclusão também é obrigatoriamente verdadeira.

* **Premissa 1:** Todo aluno de ADS sabe programar.
* **Premissa 2:** Bruna é aluna de ADS.
* **Conclusão:** Logo, Bruna sabe programar.
* **Veredito:** Note que a conclusão "salta" das premissas de forma necessária. Se aceitamos as duas primeiras frases, não temos como negar a terceira.

### B) Argumento Inválido (Sofisma/Falácia)
Mesmo que as frases pareçam verdadeiras isoladamente, se a estrutura não for conexa, o argumento é inválido. É o processo de derivar a conclusão a partir das premissas usando regras lógicas.

* **Premissa 1:** Se um computador está sem bateria, ele desliga.
* **Premissa 2:** O computador de João está desligado.
* **Conclusão:** Logo, o computador de João está sem bateria.
* **Veredito:** Este argumento é **inválido**. Por quê? Porque existem outros motivos para um computador estar desligado (ele pode estar quebrado, ou apenas fechado). A estrutura não garante a conclusão.

### C) Verdade vs. Validade
A lógica não julga se as frases são "verdades reais" do mundo, mas se a estrutura do pensamento é correta.

* **Argumento Válido com frases Falsas:**
    * **P1:** Todo gato voa. (Falso)
    * **P2:** Garfield é um gato. (Verdadeiro)
    * **C:** Logo, Garfield voa. (Falso)
* **Veredito:** O argumento é **Válido**. Embora a conclusão seja mentirosa no mundo real, ela é uma consequência lógica perfeita das premissas apresentadas.


## 2. Regras de Inferência: O Motor da Dedução

As regras de inferência são formas de argumentos válidos que servem como "atalhos" para não precisarmos fazer tabelas-verdade gigantes.

### Aplicação no Dia a Dia

* **Arquitetura de Microserviços:** O Silogismo Hipotético é a base para entender dependências entre serviços (Se o Serviço A falha, o B falha, e consequentemente o C também).
* **Sistemas Especialistas (IA):** Motores de inferência em IAs clássicas usam Modus Ponens para chegar a diagnósticos médicos ou técnicos a partir de sintomas inseridos pelo usuário.

### A) Modus Ponens (Afirmação do Antecedente)

O Modus Ponens (expressão em latim que significa "o modo que afirma") é uma regra de dedução clássica da lógica proposicional. Ele estabelece que, se uma condicional é verdadeira e a sua condição (o antecedente) também é verdadeira, então o resultado (o consequente) obrigatoriamente deve ser verdadeiro. É a regra mais comum na programação (if p then q). Se a condição ocorre, o resultado é disparado.
* Premissa 1: $p \rightarrow q$ (Se chover, a rua molha)
* Premissa 2: $p$ (Choveu)
* Conclusão: $\therefore q$ (Logo, a rua molhou)
* **Exemplo Prático:**
  1. Se o usuário digitar a senha correta ($p$), então o acesso é liberado ($q$).
  2. O usuário digitou a senha correta ($p$).
  3. **Conclusão:** O acesso está liberado ($\therefore q$).

Se você assume que a premissa $p \rightarrow q$ é uma regra válida (o que elimina a Linha 2, onde a regra falha) e você constata que $p$ é verdadeiro (eliminando as linhas 3 e 4, onde não chove), a única realidade lógica que sobra é a Linha 1. Consequentemente, a variável $q$ ("a rua molha") é forçada a ser Verdadeira.Esta regra é chamada de "Afirmação do Antecedente" porque o motor da dedução lógica é justamente a Premissa 2, onde nós afirmamos positivamente que a condição $p$ (o antecedente da frase) aconteceu.

### B) Modus Tollens (Negação do Consequente)

O Modus Tollens (do latim "o modo que nega") é outra regra clássica de dedução lógica. Ele estabelece que, se uma regra condicional é verdadeira e o seu resultado (consequente) não aconteceu, então é obrigatório concluir que a condição inicial (antecedente) também não aconteceu. Trabalha com a lógica reversa. Se o resultado esperado não aconteceu, a causa necessária também não ocorreu.
* Premissa 1: $p \rightarrow q$ (Se há fogo, há fumaça)
* Premissa 2: $\neg q$ (Não há fumaça)
* Conclusão: $\therefore \neg p$ (Logo, não há fogo)
* **Exemplo Prático:**
  1. Se o sensor detectar fumaça ($p$), então o alarme toca ($q$).
  2. O alarme não está tocando ($\neg q$).
  3. **Conclusão:** O sensor não detectou fumaça ($\therefore \neg p$).
 
O raciocínio do Modus Tollens nos leva diretamente à Linha 4 da tabela:

1. Assumimos que a regra geral é verdadeira ($p \rightarrow q$ = V). Isso nos faz descartar imediatamente a Linha 2, pois lá a regra falhou.
2. A nossa Premissa 2 afirma com certeza que "Não há fumaça" ($q$ é Falso). Isso nos obriga a descartar as Linhas 1 e 3, pois nelas $q$ é Verdadeiro.
3. A única linha que sobra na tabela é a Linha 4.
4. Se olharmos para a Linha 4, qual é o valor obrigatório de $p$ (fogo)? Ele é Falso.

Por isso o Modus Tollens funciona: ao negar o consequente (dizer que não há fumaça), a estrutura lógica te força a negar o antecedente para que a regra continue fazendo sentido. Se houvesse fogo, teria fumaça; como não há fumaça, é impossível haver fogo.
         
### C) Silogismo Hipotético (Regra da Transitividade)

Para demonstrar o Silogismo Hipotético (também chamado de Lei da Transitividade), precisamos expandir o seu exemplo. Esta regra lógica diz que podemos "conectar" duas condicionais em cadeia se o resultado (consequente) da primeira for a causa (antecedente) da segunda. Permite conectar três ou mais proposições em uma sequência lógica. Muito usado em fluxogramas de sistemas.
* Premissa 1: $p \rightarrow q$
* Premissa 2: $q \rightarrow r$
* Conclusão: $\therefore p \rightarrow r$
* **Exemplo Prático:**
  1. Se o servidor cair ($p$), o site fica offline ($q$).
   2. Se o site ficar offline ($q$), a empresa perde vendas ($r$).
  3. **Conclusão:** Se o servidor cair, a empresa perde vendas ($\therefore p \rightarrow r$).
 
O Silogismo Hipotético é um atalho lógico. Ele nos permite cortar o intermediário (o site ficar offline) e ligar diretamente a causa inicial ao resultado final. Se o evento A engatilha o B, e o B engatilha o C, então é uma certeza lógica que o evento A resulta no evento C.É exatamente como o princípio matemático da transitividade: Se $x = y$ e $y = z$, então obrigatoriamente $x = z$.

## 3. Lógica de Predicados e Quantificadores 

Até agora, tratamos as frases como blocos fechados. A **Lógica de Predicados** permite "olhar dentro" da frase, analisando sujeitos e propriedades.

### Aplicação no Dia a Dia
* **Banco de Dados (SQL):** Quando usamos SELECT * FROM usuarios WHERE status = 'ativo', estamos aplicando um predicado. O comando ALL no SQL equivale ao $\forall$ e o EXISTS ao $\exists$.
* **Validação de Formulários:** Verificar se todos os campos obrigatórios estão preenchidos ($\forall$) ou se existe algum caractere inválido na senha ($\exists$).

### A) O que é um Predicado?
É uma afirmação sobre um sujeito ($x$). Na computação, pense no predicado como uma **função booleana** que retorna V ou F.
* **Exemplo:** $P(x)$ em que $P$ é o predicado "é par".
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

### Aplicação no Dia a Dia
* **Testes Unitários (QA):** Para refutar a tese de que "o software está livre de bugs" ($\forall$), o testador só precisa provar que "existe um bug" ($\exists$). É a base do pensamento de quem trabalha com qualidade de software.
* **Filtros de Busca:** Ao negar um filtro de "Exibir apenas produtos em estoque", o sistema deve ser capaz de entender logicamente que deve buscar "Todos os produtos que NÃO estão em estoque".

### A) Negando o "Todo" ($\forall$)
Negar que **todos** fazem algo é o mesmo que dizer que **pelo menos um** não faz.
* **Regra:** $\neg (\forall x, P(x)) \equiv \exists x, \neg P(x)$
* A negação de que para todo $x$, $P(x)$ é verdadeiro, é equivalente a dizer que existe algum $x$ tal que $P(x)$ não é verdadeiro.
* Dizer que nem todos os alunos chegaram cedo é o mesmo que dizer que existe pelo menos um aluno que não chegou cedo.
* **Exemplo:**
    * Frase: "Todos os arquivos foram salvos."
    * Negação: "Não é verdade que todos os arquivos foram salvos" $\equiv$ "**Existe algum** arquivo que **não** foi salvo."

### B) Negando o "Existe" ($\exists$)
Negar que **existe pelo menos um** é o mesmo que dizer que **ninguém/nenhum** faz.
* **Regra:** $\neg (\exists x, P(x)) \equiv \forall x, \neg P(x)$
* A negação de que existe um $x$ tal que $P(x)$ é verdadeiro, é equivalente a dizer que, para todo $x$, $P(x)$ é falso.
* Dizer que não existe nenhum erro no código é o mesmo que dizer que todos os trechos de código não possuem erro (estão corretos).
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
    * em que $A(x)$ é "x é aluno de ADS" e $S(x)$ é "x estuda Python".
