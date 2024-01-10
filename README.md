# Desenvolvimento

## Instruções do projeto

Crie um banco de dados, adicione tabelas e determine quais são os atributos de cada uma. Em seguida, execute um trigger que se relacione com algum comando, como insert, select, delete ou update.



CREATE TABLE disciplinas (      <br/>
id_disciplina INT AUTO_INCREMENT PRIMARY KEY,   <br/>
nome_disciplina VARCHAR(50) NOT NULL,   <br/>
nome_professor VARCHAR(50) NOT NULL    <br/>
)   <br/>

CREATE TABLE alunos (   <br/>
id_aluno INT AUTO_INCREMENT PRIMARY KEY,    <br/>
nome_aluno VARCHAR(50) NOT NULL,   <br/>
disciplina_id INT,    <br/>
CONSTRAINT FOREIGN KEY (disciplina_id) REFERENCES disciplinas (id_disciplina   <br/>
)    <br/>

CREATE TABLE aviso (   <br/>
id_aviso INT AUTO_INCREMENT PRIMARY KEY,    <br/>
mensagem VARCHAR(100)    <br/>
)   <br/>

CREATE TRIGGER inserir_dados  <br/>
AFTER INSERT    <br/>
ON alunos FOR EACH ROW    <br/>
BEGIN    <br/>
IF NEW.disciplina_id IS NULL THEN    <br/>
INSERT INTO aviso(id_aviso, mensagem)   <br/>
VALUES    <br/>
(NEW.id,CONCAT(Oi ,NEW.nome_aluno, você não possui disciplina ainda))    <br/>
END IF   <br/>
END     <br/>
INSERT INTO disciplinas(nome_disciplina, nome_professor) VALUES ('Banco de dados', 'Maria Alves')    <br/>
INSERT INTO disciplinas (nome_disciplina, nome_professor) VALUES ('Python', 'Pietro Souza')   <br/>
INSERT INTO disciplinas (nome_disciplina, nome_professor) VALUES ('POO', 'Bia Tavares')   <br/>
INSERT INTO alunos (nome_aluno, disciplina_id) VALUES ('Cleiton', 2)   <br/>
INSERT INTO alunos (nome_aluno, disciplina_id) VALUES ('Carol', NULL)   <br/>
INSERT INTO alunos (nome_aluno, disciplina_id) VALUES ('Ruan', 2)   <br/>
INSERT INTO alunos (nome_aluno, disciplina_id) VALUES ('Gabi', 1)   <br/>
INSERT INTO alunos (nome_aluno, disciplina_id) VALUES ('Rian', NULL)   <br/>
INSERT INTO alunos (nome_aluno, disciplina_id) VALUES ('Mia', 2)   <br/>
INSERT INTO alunos (nome_aluno, disciplina_id) VALUES ('Malu', 1)   <br/>
