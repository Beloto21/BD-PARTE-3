Criando a tabela Clientes

CREATE TABLE Cidades ( id INT PRIMARY KEY, nome VARCHAR(60) NOT NULL, populacao INT );

Criando a tabela Alunos CREATE TABLE Alunos ( id INT PRIMARY KEY, nome VARCHAR(60) NOT NULL, data_nasc DATE, cidade_id INT, FOREIGN KEY(cidade_id) REFERENCES Cidades(id) );

Inserts da tabela Cidades INSERT INTO Cidades (id, nome, populacao) VALUES (1, 'São Paulo', 12176866); INSERT INTO Cidades (id, nome, populacao) VALUES (2, 'Rio de Janeiro', 6748000); INSERT INTO Cidades (id, nome, populacao) VALUES (3, 'Belo Horizonte', 2521564); INSERT INTO Cidades (id, nome, populacao) VALUES (4, 'Curitiba', 1948626); INSERT INTO Cidades (id, nome, populacao) VALUES (5, 'Porto Alegre', 1484941);

-- Inserindo a aluna Ana Silva com a cidade_id 1
INSERT INTO Alunos (id, nome, data_nasc, cidade_id) VALUES (1, 'Ana Silva', '2005-03-15', 1);

-- Inserção de Bruno Costa, que nasceu em 2004 e pertence à cidade_id 2
INSERT INTO Alunos (id, nome, data_nasc, cidade_id) VALUES (2, 'Bruno Costa', '2004-07-22', 2);

-- Cadastro da aluna Carla Santos, nascida em 2006, com cidade_id 3
INSERT INTO Alunos (id, nome, data_nasc, cidade_id) VALUES (3, 'Carla Santos', '2006-01-30', 3);

-- Adicionando Diego Pereira à tabela, com data de nascimento em 2005 e cidade_id 4
INSERT INTO Alunos (id, nome, data_nasc, cidade_id) VALUES (4, 'Diego Pereira', '2005-12-11', 4);

-- Inclusão de Eduarda Lima, de 2004, associada à cidade_id 5
INSERT INTO Alunos (id, nome, data_nasc, cidade_id) VALUES (5, 'Eduarda Lima', '2004-05-05', 5);

-- Inserindo Felipe Almeida, nascido em 2006 e vinculado à cidade_id 1
INSERT INTO Alunos (id, nome, data_nasc, cidade_id) VALUES (6, 'Felipe Almeida', '2006-09-18', 1);

-- Cadastro de Gabriela Ferreira, nascida em 2005, da cidade_id 2
INSERT INTO Alunos (id, nome, data_nasc, cidade_id) VALUES (7, 'Gabriela Ferreira', '2005-04-20', 2);

-- Henrique Rocha, nascido em 2004, agora registrado com cidade_id 3
INSERT INTO Alunos (id, nome, data_nasc, cidade_id) VALUES (8, 'Henrique Rocha', '2004-11-03', 3);

-- Registro de Isabela Martins, com data de nascimento em 2005 e cidade_id 4
INSERT INTO Alunos (id, nome, data_nasc, cidade_id) VALUES (9, 'Isabela Martins', '2005-08-29', 4);

-- João Pedro é inserido na tabela, nascido em 2006 e pertencente à cidade_id 5
INSERT INTO Alunos (id, nome, data_nasc, cidade_id) VALUES (10, 'João Pedro', '2006-02-14', 5);

-- Adicionando Larissa Mendes, de 2005, associada à cidade_id 1
INSERT INTO Alunos (id, nome, data_nasc, cidade_id) VALUES (11, 'Larissa Mendes', '2005-06-25', 1);

-- Registro do aluno Marcos Silva, nascido em 2004 e com cidade_id 2
INSERT INTO Alunos (id, nome, data_nasc, cidade_id) VALUES (12, 'Marcos Silva', '2004-10-09', 2);

Selects Selecionar todos os dados da tabela Cidades SELECT * FROM Cidades;

Selecionar todos os dados da tabela Aluno SELECT * FROM Alunos;

Este comando seleciona todos os alunos e suas cidades correspondentes SELECT * FROM Alunos INNER JOIN Cidades on Cidades.id = Alunos.cidade_id;

Seleciona todos os alunos e suas cidades, incluindo alunos sem cidade, ordenados por nome SELECT * FROM Alunos LEFT JOIN Cidades ON Cidades.id = Alunos.cidade_id ORDER BY Alunos.nome;

-- Seleciona alunos com cidades cujo nome inicia com "Por" e nascidos após 15 de agosto de 2001
SELECT A.id AS "RA", A.nome AS "Nome", A.data_nasc AS "Data de Nascimento"
FROM Alunos A
LEFT JOIN Cidades C ON A.cidade_id = C.id
-- Filtra alunos de cidades que não possuem valor nulo e que começam com "Por"
WHERE C.nome IS NOT NULL 
AND C.nome LIKE 'Por%' 
-- Filtra apenas os alunos nascidos após a data especificada
AND A.data_nasc > '2001-08-15'
-- Ordena a lista de alunos em ordem alfabética pelo nome
ORDER BY A.nome;
