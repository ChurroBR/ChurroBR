# Session Two: Getting Better
Autora: Maria Clara Campos Profeta - 37
[toc]

## Modelagem: Aluno
>Create Scripit
````sql=
create table tb_Aluno (
  id_Aluno       int primary key auto_increment,
  nm_turma       varchar (255),
  nr_ano_letivo  integer,
  nm_aluno       varchar (255), 
  nr_chamada     integer,
  ds_sexo        varchar (255)
 );
 
 create table tb_Disciplina (
   id_Disciplina  int primary key auto_increment,
   nm_disciplina  varchar (255),
   nm_professor   varchar (255)
  );
  
  create table tb_Boletim (
    id_Boletim     int primary key auto_increment,
    id_Aluno       integer,
    id_Disciplina  integer,
    vl_notas       decimal (15,2),
    qtd_faltas     integer,
  FOREIGN KEY (id_Aluno) REFERENCES tb_Aluno(id_Aluno),
  FOREIGN KEY (id_Disciplina) REFERENCES tb_Disciplina(id_Disciplina)
 );
 ````
 >Insert Scripit
````sql=
insert into tb_Aluno (nm_turma, nr_ano_letivo, nm_aluno, nr_chamada, ds_sexo) 
      values ('3° Ano B', 2011, 'Manuela Avila Bellucci', 25, 'Feminino'),
             ('5° Ano A', 2021, 'Luis Fillipi Moreira', 22, 'Masculino'),
             ('9° Ano D', 2019, 'luana Ferrari Conte' , 20, 'Feminino');
                      
 insert into tb_Disciplina (nm_disciplina, nm_professor)
      values ('Português', 'Nayane'),
             ('Matemática', 'Mauro'),
             ('Ciências', 'Marcia'),
             ('História', 'Camila'),
             ('Geografia', 'Luccas');
             
  insert into tb_Boletim (id_Aluno, id_Disciplina, vl_notas, qtd_faltas)
       values (1, 1, '10', 2),
              (1, 2, '9', 1),
              (1, 3, '7', 3),
              (1, 4, '8', 1),
              (1, 5, '7', 0),
              (2, 1, '5', 5),
              (2, 2, '6', 3),
              (2, 3, '2', 4),
              (2, 4, '4', 3),
              (2, 5, '2', 2),
              (3, 1, '7', 2),
              (3, 2, '7', 3),
              (3, 3, '5', 2),
              (3, 4, '6', 0),
              (3, 5, '5', 1);
````
>Select Script
````sql=
--1. Selecionar aluno, turma, ano, disciplina, nota aplicando o relacionamento nas tabelas, sem filtros, ordenando por aluno.
    select A.nm_aluno,
           A.nm_turma,
           A.nr_ano_letivo,
           D.nm_disciplina,
           B.vl_notas
      from tb_Boletim      B
inner join tb_Aluno        A on A.id_Aluno = B.id_aluno
inner join tb_Disciplina   D on D.id_Disciplina = B.id_disciplina
  order by nm_aluno;
  
--2. Selecionar aluno, turma, ano, disciplina, nota aplicando o relacionamento nas tabelas, filtrando por turma e ano letivo, ordenando por nota da maior para a menor.
    select A.nm_aluno,
           A.nm_turma,
           A.nr_ano_letivo,
           D.nm_disciplina,
           B.vl_notas
      from tb_Boletim      B
inner join tb_Aluno        A on A.id_Aluno = B.id_aluno
inner join tb_Disciplina   D on D.id_Disciplina = B.id_disciplina
  order by vl_notas desc;
  
--3. Selecionar aluno, turma, ano, disciplina, nota aplicando o relacionamento nas tabelas, filtrando os alunos aprovados por ano e turma, ordenando por ano, turma e chamada.
    select A.nm_aluno,
           A.nm_turma,
           A.nr_ano_letivo,
           A.nr_chamada,
           A.tb_status,
           D.nm_disciplina,
           B.vl_notas
      from tb_Boletim      B
inner join tb_Aluno        A on A.id_Aluno = B.id_aluno
inner join tb_Disciplina   D on D.id_Disciplina = B.id_disciplina
     where tb_status = 'Aprovado'
  order by nr_ano_letivo, 
           nm_turma, 
           nr_chamada asc;
           
--4. Selecionar aluno, turma, ano aplicando o relacionamento nas tabelas, filtrando os alunos reprovados por ano e turma.
    select A.nm_aluno,
           A.nm_turma,
           A.nr_ano_letivo,
           A.tb_status
      from tb_Boletim      B
inner join tb_Aluno        A on A.id_Aluno = B.id_aluno
inner join tb_Disciplina   D on D.id_Disciplina = B.id_disciplina
     where tb_status = 'Reprovado';
````

>5. Crie mais 5 consultas personalizadas conforme sua vontade que explore filtros como: >, >=, <, <=, =, <>, LIKE, IN, BETWEEN, Funções de Texto/Número/Data
````sql=
--Selecionar Aluno, Aplicando o relacionamento nas tabelas, com os nomes que tenham a letra 'N'.
    select A.nm_aluno
      from tb_Boletim      B
inner join tb_Aluno        A on A.id_Aluno = B.id_aluno
inner join tb_Disciplina   D on D.id_Disciplina = B.id_disciplina
     where nm_aluno like '%n%';
     
--Consultar todas as notas que sejam maior ou igual a 3.
    select*
      from tb_Boletim      B
inner join tb_Aluno        A on A.id_Aluno = B.id_aluno
inner join tb_Disciplina   D on D.id_Disciplina = B.id_disciplina
     where qtd_faltas >= 3 ;

--Consultar todos os alunos que sejam do sexo masculino.
    select*
      from tb_Boletim      B
inner join tb_Aluno        A on A.id_Aluno = B.id_aluno
inner join tb_Disciplina   D on D.id_Disciplina = B.id_disciplina
     where ds_sexo = 'Masculino' ;
     
--Consultar o ano letivo que seja igual o maior a 2019.
    select*
      from tb_Boletim      B
inner join tb_Aluno        A on A.id_Aluno = B.id_aluno
inner join tb_Disciplina   D on D.id_Disciplina = B.id_disciplina
     where nr_ano_letivo >= 2019 ;
          
--Consultar todos os alunos que sejam do sexo feminino.
    select*
      from tb_Boletim      B
inner join tb_Aluno        A on A.id_Aluno = B.id_aluno
inner join tb_Disciplina   D on D.id_Disciplina = B.id_disciplina
     where ds_sexo = 'Feminino' ;
````

>Delet
````sql=
DELET FROM tb_boletim
      WHERE id_Aluno = 3;
````