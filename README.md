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


## -- SE QUISER FAZER UMA SEQUENCIA COM LIMITES

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
