## exercicios-de-postgre
#criando tabelas por meio de script

CREATE TABLE IF NOT EXISTS departamento (

	--atributos
	nome varchar(60),
	num_dept serial not null,
	
	--chave primaria
	CONSTRAINT departamento_pkey PRIMARY KEY(num_dept)
	
	-- restriçoes
	

);

CREATE TABLE IF NOT EXISTS empregado(
	
	--atributos
	matricula serial not null,
	nome varchar(60),
	salario real,
	num_dept integer,
	
	--chave primaria
	CONSTRAINT empregado_pkey PRIMARY KEY (matricula),
	
	-- chave estrangeira
	CONSTRAINT empregado_fkey FOREIGN KEY (num_dept)
	REFERENCES departamento(num_dept),
	
	--restriçoes
	CONSTRAINT empregado_check CHECK (salario>1044.99)

);


# -- SE QUISER FAZER UMA SEQUENCIA COM LIMITES

CREATE sequencial
--incrementa de 1 em 1 poderia ser 2 em 2 ou 5 em 5
INCREMENT 1
--limite minimo
MINVALUE 1111
--limite maximo
MAXVALUE 1500
-- começa no limite minimo, mas poderia ser depois por exemplo 1150
START 1111
--guarda no cache o ultimo valor
CACHE 1;

#-- para usar a sequencia

CREATE TABLE IF NOT EXISTS tabela (
-- a variavel codigo vai receber o valor da sequencia
codigo INT DEFAULT NEXTVAL('sequencial'),
nome VARCHAR(20),
-- a variavel codigo sera a chave primaria da tabela
CONSTRAINT tabela_pkey PRIMARY KEY (codigo)

);

##-- para inserir dados na tabela empregado

INSERT INTO empregado (nome, salario, numero_dpto)
VALUES ('Ricarda Joana', 1800, 2), ('Mane Cabral', 5000000, 1), ('Bolsonaro',3500000,2)
,('ACM Neto', 100000, 4);
 
 ##-- para exibir todos os dados da tabela
 
 SELECT * FROM empregado
 
## -- criação de nova tabela que vai guardar dados de outras
 
 CREATE TABLE IF NOT EXISTS dept_inf(
	codigo SERIAL NOT NULL,
	nome VARCHAR (60),
	somaSalario Real,
	CONSTRAINT dept_inf_pkey PRIMARY KEY (codigo)

);

#-- inserindo dados de outras tabelas naquela recem criada

-- vai inserir na tabela dept_inf
INSERT INTO dept_inf (nome,num_dept, somaSalario)

##-- dados da tabela departamento.nome  somando os salarios

SELECT D.nome, COUNT(*), SUM(salario) FROM empregado E,
departamento D WHERE D.num_dept = E.num_dept GROUP BY D.nome
##-- quando tiver mais de 2 registros

HAVING COUNT(*) >2

--quando quiser fazer alguma atualização na tabela

-- vai atualizar o salario na tabela empregado da tupla matricula= 1

UPDATE empregado SET salario=salario*1.2 WHERE matricula=1

-- ordena a tabela

SELECT * FROM empregado ORDER BY matricula

-- condição para apagar dados de uma tabela

DELETE FROM empregados WHERE salario > 5000

-- SELECIONA TUPLAS COM CONDIÇÃO

SELECT nome, salario FROM empregado 
WHERE NUMERO_DPTO = 2 ORDER BY matricula

SELECT nome, salario FROM empregado 
WHERE NUMERO_DPTO = 2 AND SALARIO >=3000 ORDER BY matricula



