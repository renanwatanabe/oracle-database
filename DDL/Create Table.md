#DDL CREATE TABLE

Criacao de tabela simples:

``` SQL
CREATE TABLE TB_PERSONAGEM(
PERSONAGEM_ID NUMBER,
NICK VARCHAR2(250),
NIVEL NUMBER(3),
DATA_CRIACAO DATE);
```

###Tipos de Constraints :###

* NOT NULL

* UNIQUE

* CHECK

* PRIMARY KEY

* FOREIGN KEY

----------------------------------
##NOT NULL##
Descrição:  Restrição para nao poder gravar valor null na tabela apenas.

Exemplos de criação:

**NOT NULL In line**
```SQL
CREATE TABLE TB_PERSONAGEM()
NICKNAME VARCHAR2(100) NOT NULL  /* Cria uma constraint anonima(gerada com nome pelo oracle) 
                                    not null na coluna nickname. */
);

CREATE TABLE TB_PERSONAGEM(
NICKNAME VARCHAR2(100) CONSTRAINT NICKNAME_NN NOT NULL   /* Cria uma constraint not null com o 
                                                          nome 'NICKNAME_NN' na coluna Nickname. */
);
```

**NOT NULL Out of Line**

Nao Existe!!!

**NOT NULL Exemplo de Insert:**
```SQL
INSERT INTO TB_PERSONAGEM VALUES('RENAN'); -- Insere normalmente o valor 'Renan';
INSERT INTO TB_PERSONAGEM VALUES(''); -- DA ERRO, pois '' eh null.
INSERT INTO TB_PERSONAGEM VALUES(null); -- DA ERRO, pois eh null.
INSERT INTO TB_PERSONAGEM VALUES(' ');  -- permite inserir,pois ' ' nao eh null.
```

------------------------------------------------------------------------------------------
##UNIQUE##
Descricao: nao permite existir 2 valores iguais, se for null deixa qnts quiser, pode ser usado como juncao de colunas tbm.

**UNIQUE In line**
```SQL

--UNICA COLUNA
CREATE TABLE tb_personagem(NOME varchar(5) UNIQUE) -- Cria uma constraint anonima unique na coluna NOME;

CREATE TABLE TB_PERSONAGEM(
NOME VARCHAR2(100) CONSTRAINT NOME_UN UNIQUE); /*Cria uma constraint UNIQUE com o 
                                                    nome 'NOME_UN' na coluna Nickname. */


--NAO EH POSSIVEL CRIAR UNIQUE IN LINE COM MULTIPLAS COLUNAS.
CREATE TABLE TB_PERSONAGEM(
NOME varchar(5) UNIQUE,
IDADE NUMBER UNIQUE
);  -- OS UNIQUES SAO INDEPENDENTES.
```


**UNIQUE Out of Line**
















IN LINE:

CREATE TABLE TB_PERSONAGEM(                    
PERSONAGEM_ID NUMBER PRIMARY KEY   ---Cria uma constraint anonima na coluna personagem_id.
);


CREATE TABLE TB_PERSONAGEM(
PERSONAGEM_ID NUMBER CONSTRAINT PERSONAGEM_ID_PK PRIMARY KEY   -- Cria uma constraint com nome PERSONAGEM_ID_PK na coluna PERSONAGEM_ID.
);


CREATE TABLE TB_PERSONAGEM()
NICKNAME VARCHAR2(100) NOT NULL  - Cria uma constraint anonima not null na coluna nickname.
);

CREATE TABLE TB_PERSONAGEM()
NICKNAME VARCHAR2(100) CONSTRAINT NICKNAME_NN NOT NULL   - Cria uma constraint not null com o nome 'NICKNAME_NN' na coluna Nickname.
);




Out of Line:

CREATE TABLE TB_PERSONAGEM(                    
PERSONAGEM_ID NUMBER,
PRIMARY KEY (PERSONAGEM_ID)   ---Cria uma constraint anonima na coluna personagem_id.
);

CREATE TABLE TB_PERSONAGEM(
PERSONAGEM_ID NUMBER,
CONSTRAINT PERSONAGEM_ID_PK PRIMARY KEY(PERSONAGEM_ID) -- Cria uma constraint com nome PERSONAGEM_ID_PK na coluna PERSONAGEM_ID.
);

*Nao existe out of line para constraints not null.
