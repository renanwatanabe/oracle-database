##Tipos de dados Oracle##





###CHAR###

**Char**           | Valores
-------------------|------------------------------------------------------------------------------
Nome               | CHAR
Descricao          | Tipo de dado alfanumérico.
Tamanho Default    | Ao criar uma coluna como 'SEXO CHAR', o valor Default da coluna será CHAR(1).
Tamanho Maximo     | 2000 bytes.
Observacoes        | Ao inserir um registro, será sempre considerado o tamanho máximo do campo completando com espaços em branco em branco caso o valor seja menor que o da coluna.


Exemplos :
```SQL
CREATE TABLE TB_PESSOA(NOME char(5));

INSERT INTO TB_PESSOA  VALUES(1);  --insere o caractere '1' com 4 espacos a direita '1    ';
INSERT INTO TB_PESSOA  VALUES('a'); --insere o caractere 'a' com 4 espacos a direita 'a    ';
INSERT INTO TB_PESSOA VALUES(''); --realmente insere um registro no banco, porem esse valor fica como (null),se inserir 5 vezes, tera 5 linhas com valor null.
INSERT INTO TB_PESSOA_VALUES(' ') -- insere um espaco em branco, porém em vez de ' ', vai ficar '     ';
SELECT LENGTH(NOME) FROM TB_PESSOA; -- retorna o valor 5, mesmo que o nome cadastrado seja 'a'('a    ');
INSERT INTO TB_PESSOA  VALUES('ééééé'); --Dá ERRO! Mesmo que o varchar2(5) seja tamanho 5, são 5 bytes de capacidade,
                                        --porém o caractere 'é' possui 3 bytes cada.
```

###VARCHAR2###

**VARCHAR2**           | Valores
-------------------|------------------------------------------------------------------------------
Nome | VARCHAR2
Descricao | Tipo de dado caractere.
Tamanho default| Nao existe 'NOME VARCHAR2', voce sempre tera que passar um argumento, ou seja 'NOME VARCHAR2(1)'
Tamanho Maximo | 4000 bytes.
OBSERVACOES: 

Exemplos:
```SQL
CREATE TABLE TB_PESSOA(
NOME VARCHAR2(10)
);
```
```SQL
INSERT INTO TB_PESSOA  VALUES(130);  //insere os caracteres '130';
INSERT INTO TB_PESSOA  VALUES('abc'); //insere o caractere 'abc';
```

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
