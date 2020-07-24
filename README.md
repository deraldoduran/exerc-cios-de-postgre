# exerc-cios-de-postgre
criando tabelas por meio de script

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
