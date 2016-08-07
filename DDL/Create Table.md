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

NULL / NOT NULL -> nao permite inserir null, '' nas tabelas.
UNIQUE -> nao permite existir 2 valores iguais, se for null deixa qnts quiser, pode ser usado como juncao de colunas tbm.
PRIMARY KEY -> eh a juncao de Not null com unique.
FOREIGN KEY


CHECK


Constraints(restricao): 
Existem 2 tipos de criacao: 'in line' e 'out of line'



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