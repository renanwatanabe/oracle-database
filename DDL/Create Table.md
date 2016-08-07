#DDL CREATE TABLE

###Tipos de Constraints :###

* NOT NULL

* UNIQUE

* CHECK

* PRIMARY KEY

* FOREIGN KEY

----------------------------------
##NOT NULL##
Descrição:  Restrição para nao poder gravar valor null na tabela apenas.

**In line**
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

**Out of Line**

Nao Existe!!!

**Exemplo de Insert:**
```SQL
INSERT INTO TB_PERSONAGEM VALUES('RENAN'); -- Insere normalmente o valor 'Renan';
INSERT INTO TB_PERSONAGEM VALUES(''); -- DA ERRO, pois '' eh null.
INSERT INTO TB_PERSONAGEM VALUES(null); -- DA ERRO, pois eh null.
INSERT INTO TB_PERSONAGEM VALUES(' ');  -- permite inserir,pois ' ' nao eh null.
```

------------------------------------------------------------------------------------------
##UNIQUE##
Descricao: nao permite existir 2 valores iguais, se for null deixa qnts quiser, pode ser usado como juncao de colunas tbm.

**In line**
```SQL
--UNICA COLUNA
CREATE TABLE tb_personagem(NOME varchar(5) UNIQUE) -- Cria uma constraint anonima unique na coluna NOME;

CREATE TABLE TB_PERSONAGEM(
NOME VARCHAR2(100) CONSTRAINT NOME_UN UNIQUE); /*Cria uma constraint UNIQUE com o 
                                                    nome 'NOME_UN' na coluna Nickname. */


--NAO EH POSSIVEL CRIAR UNIQUE IN LINE COM MULTIPLAS COLUNAS, Porem pode ser usado unique para varias colunas separadas.
CREATE TABLE TB_PERSONAGEM(
NOME varchar(5) UNIQUE,
IDADE NUMBER UNIQUE
);  -- OS UNIQUES SAO INDEPENDENTES.
```


**Out of Line**
```SQL
CREATE TABLE TB_PERSONAGEM(
NOME varchar(5),
UNIQUE(NOME)    -- Cria uma constraint anonima unique na coluna NOME;
);

CREATE TABLE TB_PERSONAGEM(
NOME varchar(5),
CONSTRAINT NOME_UQ UNIQUE(NOME) /*Cria uma constraint UNIQUE com o 
                                                    nome 'NOME_UN' na coluna Nickname. */
);
```

**Multiplas colunas 

```SQL
CREATE TABLE TB_PERSONAGEM(
NOME varchar(5),
IDADE NUMBER,
UNIQUE(NOME,IDADE)    -- Cria uma constraint anonima unique na coluna NOME e IDADE JUNTAS!
);

```SQL
CREATE TABLE TB_PERSONAGEM(
NOME varchar(5),
IDADE NUMBER,
CONSTRAINT NOME_IDADE_UQ UNIQUE(NOME,IDADE)    -- Cria uma constraint unique com o nome 'NOME_UN' na coluna NOME e IDADE JUNTAS!
);









