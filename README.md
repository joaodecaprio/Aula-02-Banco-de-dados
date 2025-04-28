# Aula-02-Banco-de-dados

CREATE TABLE alunos (
  id SERIAL PRIMARY KEY,
  nome TEXT NOT NULL,
  turma TEXT NOT NULL,
  curso TEXT NOT NULL,
  data_nascimento DATE
);

CREATE TABLE cursos (
  id SERIAL PRIMARY KEY,
  nome TEXT NOT NULL,
  duracao_anos INT
);

CREATE TABLE matriculas (
  id SERIAL PRIMARY KEY,
  aluno_id INT REFERENCES alunos(id) ON DELETE CASCADE,
  curso_id INT REFERENCES cursos(id) ON DELETE CASCADE,
  data_matricula DATE DEFAULT CURRENT_DATE
);

INSERT INTO alunos (nome, turma, curso, data_nascimento)
VALUES ('Thulio Bacco', 'T15', 'Ciencia da computacao', '2002-05-10'),
       ('Caue Meyer', 'T15', 'ADM TECH', '2003-08-15'),
       ('Henrique Diniz', 'T15','Engenharia de software', '2003-06-11'),
       ('Carlos Eduardo Quaglia','T15','Engenharia de software','2005-05-07' ),
       ('Antonio Cillo', 'T15','Engenharia da Computacao','2007-06-04'),
       ('Rafael Cabral','T15', 'Engenharia de software', '2006-05-30'),
       ('Emanuelly Diaz','T15', 'Engenharia de software', '2006-02-13'),
       ('Maria Lima', 'T15', 'Engenharia de software','2005-11-02'),
       ('Joao Agmont', 'T15', 'Ciencia da computacao', '2006-06-11'),
       ('Luiz Hinuy','T15', 'Engenharia de software','2005-12-31' );

      INSERT INTO cursos (nome, duracao_anos)
      VALUES ('Engenharia de software', 4),
       ('Ciencia da computacao', 4),
       ('ADM TECH', 4),
       ('Engenharia da computacao', 4);
       
INSERT INTO matriculas (aluno_id, curso_id)
VALUES (1, 4),
       (2, 3),
       (3, 1),
       (4, 1),
       (5, 2),
       (6, 1),
       (7, 1),
       (8, 1),
       (9, 2),
       (10,1);
      
      SELECT * FROM alunos;

      SELECT * FROM cursos;

      SELECT a.nome AS aluno, c.nome AS curso, m.data_matricula
FROM matriculas m
JOIN alunos a ON m.aluno_id = a.id
JOIN cursos c ON m.curso_id = c.id;
