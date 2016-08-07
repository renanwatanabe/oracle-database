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


##NOT NULL##
Descricao:  restrição para nao poder gravar null na tabela.

Exemplo de criacao:

**NOT NULL In line**
```SQL
CREATE TABLE TB_PERSONAGEM()
NICKNAME VARCHAR2(100) NOT NULL  -- Cria uma constraint anonima not null na coluna nickname.
);

CREATE TABLE TB_PERSONAGEM(
NICKNAME VARCHAR2(100) CONSTRAINT NICKNAME_NN NOT NULL   -- Cria uma constraint not null com o 
                                                         -- nome 'NICKNAME_NN' na coluna Nickname.
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


##UNIQUE##
Descricao: nao permite existir 2 valores iguais, se for null deixa qnts quiser, pode ser usado como juncao de colunas tbm.

**UNIQUE In line**
```SQL
CREATE TABLE tb_personagem(NOME varchar(5) UNIQUE) -- Cria uma constraint anonima unique na coluna NOME;

CREATE TABLE TB_PERSONAGEM(
NOME VARCHAR2(100) CONSTRAINT NICKNAME_UN UNIQUE  -- Cria uma constraint UNIQUE com o 
                                                         -- nome 'NICKNAME_UN' na coluna Nickname.

```

















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
