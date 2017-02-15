create table editora
(edi_codigo number (10),
edi_nome varchar2(70) not null)
/

create table autor
(aut_matricula number (10),
aut_nome varchar2 (50) not null,
aut_cpf varchar2(12) not null,
aut_dtnasc date not null,
aut_nascionalidade varchar2(30))
/

create table livro
(liv_codigo number(10),
liv_titulo varchar2(70),
liv_preco number(7,2),
liv_lancamento date,
edi_codigo number(10),
ass_sigla char(3) not null)
/

create table assunto
(ass_sigla char(3),
ass_descricao varchar2 (20))
/

alter table editora
add(constraint editora_edi_codigo_pk primary key(edi_codigo))
/

alter table livro
add (constraint livro_liv_codigo_pk primary key (liv_codigo))
/

alter table autor
add(constraint autor_aut_matricula_pk primary key (aut_matricula))
/

alter table assunto
add(constraint assunto_ass_sigla_pk primary key(ass_sigla))
/


alter table livro
add(constraint livro_edi_codigo_fk foreign key(edi_codigo) references editora(edi_codigo))
/


alter table livro
add (constraint livro_ass_sigla_fk foreign key (ass_sigla) references assunto(ass_sigla))
/


create table escreve
(liv_codigo number(10),
aut_matricula number (10),
constraint escreve_liv_aut_pk primary key(liv_codigo,aut_matricula),
constraint escreve_liv_codigo_fk foreign key (liv_codigo) references livro (liv_codigo),
constraint escreve_liv_aut_matricula_fk foreign key (aut_matricula)
references autor(aut_matricula));

