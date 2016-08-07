##Tipos de dados Oracle##





###CHAR###

**Char**           | Valores
-------------------|------------------------------------------------------------------------------
Nome               | CHAR
Descrição          | Tipo de dado alfanumérico.
Tamanho Default    | Ao criar uma coluna como 'SEXO CHAR', o valor Default da coluna será CHAR(1).
Tamanho Máximo     | CHAR(2000), ou seja, 2000 bytes.
Observações        | Ao inserir um registro, será sempre considerado o tamanho máximo do campo completando com espaços em branco caso o valor seja menor que o da coluna.

Exemplos :
```SQL
CREATE TABLE TB_PESSOA(NOME char(5));

INSERT INTO TB_PESSOA VALUES(1);  --insere o caractere '1' com 4 espacos a direita '1    ';
INSERT INTO TB_PESSOA VALUES('a'); --insere o caractere 'a' com 4 espacos a direita 'a    ';
INSERT INTO TB_PESSOA VALUES(''); --realmente insere um registro no banco, porem esse valor fica como (null), se inserir 5 vezes, 
                                  --existirão 5 linhas com valor null.
INSERT INTO TB_PESSOA VALUES(null); --Permite,cria e insere um registro com valor null;                                  
INSERT INTO TB_PESSOA VALUES(' ') -- insere um espaco em branco, porém em vez de ' ', vai ficar '     ';
INSERT INTO TB_PESSOA VALUES('ééééé'); --Dá ERRO! Mesmo que o varchar2(5) seja tamanho 5, são 5 bytes de capacidade,
                                        --porém o caractere 'é' possui 3 bytes cada.
                                        
SELECT LENGTH(NOME) FROM TB_PESSOA; -- retorna o valor 5, mesmo que o nome cadastrado seja 'a'('a    ');
```

###VARCHAR2###

**VARCHAR2**           | Valores
-------------------|------------------------------------------------------------------------------
Nome | VARCHAR2
Descricao | Tipo de dado alfanumérico.
Tamanho default| Não existe 'NOME VARCHAR2', voce sempre tera que passar um argumento, ou seja 'NOME VARCHAR2(1)'
Tamanho Maximo | VARCHAR(4000), ou seja, 4000 bytes.
OBSERVACOES: Ao inserir um registro, ele ocupara apenas o tamanho do mesmo,ou seja, se inserir 'renan', ira gravar 'renan' sem os espacos em branco.

Exemplos:
```SQL
CREATE TABLE TB_PESSOA(NOME VARCHAR2(5));

INSERT INTO TB_PESSOA  VALUES(130);  --insere os caracteres '130';
INSERT INTO TB_PESSOA  VALUES('abc'); --insere o caractere 'abc';
INSERT INTO TB_PESSOA VALUES(''); --realmente insere um registro no banco, porem esse valor fica como (null), se inserir 5 vezes, 
                                  --existirão 5 linhas com valor null.
INSERT INTO TB_PESSOA VALUES(null); --Permite,cria e insere um registro com valor null; 
INSERT INTO TB_PESSOA VALUES(' ') -- insere um espaco em branco com valor ' ', repare que ' ' NAO EH NULL.
INSERT INTO TB_PESSOA VALUES('ééééé'); --Dá ERRO! Mesmo que o varchar2(5) seja tamanho 5, são 5 bytes de capacidade,
                                        --porém o caractere 'é' possui 3 bytes cada.
```

[TODO] NCHAR E NVARCHAR2

###NUMBER###

**NUMBER**           | Valores
-------------------|------------------------------------------------------------------------------
Nome | NUMBER
Descricao |  Coluna do tipo numerico(precisao, escala).
Tamanho Default |  Ao criar NUMBER com valor DEFAULT, sera criado NUMBER sem nenhuma precisao.  'IDADE NUMBER' , sera criado o tipo NUMBER.
Tamanho maximo | 38 digitos.
Observacoes : - If a precision is not specified, the column stores values as given. If no scale is specified, the scale is zero.
              -n defaults to the maximum value, m defaults to zero
              -The value for n can range from 1 to 38; the value for m can range from –84 to 127
 




**DATE**           | Valores
-------------------|------------------------------------------------------------------------------
Nome| DATE
Descricao | Tambem considerado como datetime, armazena o dia mes ano hora minuto e segundo.
Tamanho Default |nao existe date(1), sera sempre DATE.
tamanho maximo |
Observacoes:


Exemplos:
```SQL
CREATE TABLE TB_PESSOA(
aniversario date
);

select TO_CHAR(SYSDATE, 'DD/MM/YYYY HH24:MI:SS') as DATA_HORA from tb_pessoa;


INSERT INTO TB_PESSOA VALUES('30/06/1990');  --Ira gravar 30/06/1990 00:00:00
INSERT INTO TB_PESSOA VALUES('30-06-1990');  --Ira gravar 30/06/1990 00:00:00
INSERT INTO TB_PESSOA VALUES('06-30-1990');  --NAO ira gravar, vai dar erro.
INSERT INTO TB_PESSOA VALUES(TO_DATE('30/06/1990 21:02:59', 'DD/MM/YYYY HH24:MI:SS')); --Ira gravar 30/06/1990 21:02:59
```
