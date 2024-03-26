# Criação de Banco de Dados de Carros em Postgres
## Possui o Marca, Modelo, Cor e Ano.

```sql
-- Criar Banco de Dados
CREATE TABLE carros (
    marca VARCHAR(255),
    modelo VARCHAR(255),
    cor VARCHAR(255),
    ano int
);

-- Query para consultar todos os Carros
-- Não vai mostrar nada ainda
SELECT * FROM public."carros";

-- Query para inserir dados na tabela
INSERT INTO public."carros" (marca, modelo, cor, ano)
VALUES ('Ford', 'Mustang', 'Preto', 2024),
('Chevrolet', 'Onix', 'Vermelho', 2024);

-- Realizando a consulta mostrará os dois carros
SELECT * FROM public."carros";

-- Consultar dados especificos
-- Modelo e Ano
SELECT modelo, ano FROM public."carros";

-- Adicionar mais uma coluna a nosso banco de dados
ALTER TABLE carros
ADD valor DECIMAL;

-- Atualizar valores de uma tabela
UPDATE carros
SET cor = 'Branco'
WHERE modelo = 'Onix';
-- Para atualizar mais de uma tabela usar ( , )
UPDATE carros
SET cor = 'Branco', ano = 2023
WHERE modelo = 'Onix';

-- Para alterar o tipo de dado de uma tabela basta usar ALTER TABLE
-- ALTER TABLE é usada para atualizar, excluir ou editar.
-- Trocar o tipo do Ano de INT para VARCHAR
ALTER TABLE carros
ALTER COLUMN ano TYPE VARCHAR(4);
-- Alterar o número máximo de caracteres na coluna Cor
ALTER TABLE carros
ALTER COLUMN cor TYPE VARCHAR(30);

-- Remover uma coluna de uma tabela 
ALTER TABLE carros
DROP COLUMN valor;

-- Excluir dados de uma dados de uma tabela
DELETE FROM carros
WHERE marca = 'Chevrolet';

-- DELETAR uma TABELA do banco de dados
DROP TABLE carros;

-- Ao realizar a query de consulta, irá dar um erro 
-- ERROR: relação "public.carros" não existe
-- LINE 1: SELECT * FROM public."carros";