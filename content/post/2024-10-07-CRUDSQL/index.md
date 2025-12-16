---
title: 'Comandos Básicos em MySQL (CRUD)'
date: '2024-10-07'
slug: crud
categories: []
tags: [database, mysql, crud, tutorial, DDL, DML, SQL]
hidden: true
subtitle: ''
summary: 'Comandos básicos para manipulação de banco de dados'
authors: []
lastmod: '2024-10-11T15:11:20-03:00'
featured: no
image:
  caption: ''
  focal_point: ''
  preview_only: no
projects: []
---

## 1. [MySQL](https://www.mysql.com/) 

Sistema de gerenciamento de banco de dados relacional (RDBMS) amplamente utilizado. Ele permite que você armazene, gerencie e consulte dados de forma eficiente. Aqui estão alguns conceitos e comandos básicos sobre o MySQL:

No vídeo abaixo, segue uma demonstração destas operações no MySQL:

{{< youtube id="9sjYF3NsdJY" >}}


### Conceitos Básicos

**Banco de Dados:** Uma coleção organizada de dados.

**Tabela:** Estrutura dentro do banco de dados que armazena dados em linhas e colunas.

**Registro:** Uma linha em uma tabela, representando uma entrada de dados.

**Coluna:** Um campo dentro de uma tabela, representando um tipo específico de dado.

### Características do MySQL:

**Código Aberto:** O MySQL é um software de código aberto, embora também tenha versões comerciais.

**Suporte a Transações:** Permite operações que podem ser revertidas em caso de falhas.

**Escalabilidade:** Pode lidar com grandes volumes de dados e muitos usuários simultâneos.

**Compatibilidade:** Funciona em várias plataformas, incluindo Windows, Linux e macOS.

## Algumas Funções Úteis no MySQL

### Exibir os bancos de dados disponíveis no servidor:
```sql
SHOW DATABASES;
```

### Ativar um banco de dados:
```sql
USE nome_do_DB;
```

### Exibir as tabelas disponíveis no banco de dados:
```sql
SHOW TABLES;
```

### Obter detalhes de uma tabela específica:
```sql
DESCRIBE table_name;
```

### Ordenar dados em uma tabela:
```sql
SELECT * FROM table_name
ORDER BY column_name [ASC|DESC];
```
Exemplo:
```sql
SELECT * FROM Alunos
ORDER BY PrimeiroNome DESC;
```

---

## **DDL e DML em MySQL**

No contexto do MySQL, DDL e DML são dois subconjuntos de comandos SQL que desempenham papéis distintos na manipulação de bancos de dados.

### Comandos **DDL** (Data Definition Language):

DDL se refere à "Linguagem de Definição de Dados". Esses comandos são usados para definir e gerenciar a estrutura do banco de dados. Exemplos de comandos DDL incluem:

- **CREATE DATABASE**: Cria um banco de dados.
- **DROP DATABASE**: Apaga um banco de dados existente.
- **CREATE TABLE**: Cria uma tabela.
- **ALTER TABLE**: Altera a estrutura de uma tabela.
- **DROP TABLE**: Apaga uma tabela existente.

Exemplo de DDL:
```sql
CREATE DATABASE databasename;

DROP DATABASE databasename;

CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype,
   ....
);
```

### Comandos **DML** (Data Manipulation Language):

DML significa "Linguagem de Manipulação de Dados". Esses comandos são usados para manipular e interagir com os dados dentro das tabelas. Exemplos de comandos DML incluem:

- **INSERT INTO**: Insere um novo registro.
- **DELETE FROM**: Apaga registros de uma tabela.
- **UPDATE**: Atualiza os dados de um registro.
- **SELECT**: Seleciona registros com base em condições.

Exemplo de DML:
```sql
INSERT INTO Alunos (PrimeiroNome, SobreNome, Idade)
VALUES ('Francisco', 'Bento', 39);

DELETE FROM Alunos WHERE PrimeiroNome = 'Leonardo';

UPDATE Alunos
SET Curso = 'Engenharia'
WHERE ID = 1;

SELECT PrimeiroNome, Curso FROM Alunos;
```
 
## 2. **CRUD** 

Acrônimo que se refere às quatro operações básicas de manipulação de dados em um sistema de banco de dados. 
O termo é amplamente utilizado em desenvolvimento de software e bancos de dados. As operações incluem:

CREATE - Criar

READ - Ler

UPDATE - Atualizar

DELETE - Deletar

---

## **C**reate (Criar)  
Comandos utilizados para criação de banco de dados, tabelas e registros no MySQL:

### Criar um banco de dados:
```sql
CREATE DATABASE nome_do_DB;
```
Exemplo:
```sql
CREATE DATABASE aula2008;
```

### Criar uma tabela:
```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype,
   ....
);
```
Exemplo:
```sql
CREATE TABLE Alunos (
    ID int NOT NULL AUTO_INCREMENT,
    PrimeiroNome varchar(255) NOT NULL,
    SobreNome varchar(255),
    Idade int,
    PRIMARY KEY (ID)
);
```

### Inserir dados em uma tabela:
```sql
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);
```
Exemplo:
```sql
INSERT INTO Alunos (PrimeiroNome, SobreNome, Idade)
VALUES ('Leonardo', 'Grando', 39);
```

---

## **R**ead (Ler)  
Comandos para consultar e buscar informações no MySQL:

### Exibir todos os registros de uma tabela:
```sql
SELECT * FROM table_name;
```
Exemplo:
```sql
SELECT * FROM Alunos;
```

### Refinar a busca de colunas específicas:
```sql
SELECT column1, column2 FROM table_name;
```
Exemplo:
```sql
SELECT PrimeiroNome, Idade FROM Alunos;
```

### Busca com filtro de uma condição específica:
```sql
SELECT * FROM table_name WHERE column = 'valor';
```
Exemplo:
```sql
SELECT * FROM Alunos WHERE PrimeiroNome = 'Leonardo';
```

---

## **U**pdate (Atualizar)  
Comandos para atualizar registros existentes no MySQL:

### Atualizar registros de uma tabela:
```sql
UPDATE table_name
SET column1 = 'value1', column2 = 'value2'
WHERE condition;
```
Exemplo:
```sql
UPDATE Alunos
SET PrimeiroNome = 'Joselito', Idade = 40
WHERE ID = 1;
```

---

## **D**elete (Deletar)  
Comandos para remover registros ou estruturas no MySQL:

### Remover um registro específico:
```sql
DELETE FROM table_name WHERE condition;
```
Exemplo:
```sql
DELETE FROM Alunos WHERE PrimeiroNome = 'Leonardo';
```

### Deletar uma tabela inteira:
```sql
DROP TABLE table_name;
```
Exemplo:
```sql
DROP TABLE Alunos;
```

### Deletar um banco de dados:
```sql
DROP DATABASE nome_do_DB;
```
Exemplo:
```sql
DROP DATABASE aula2008;
```

## UPDATE 11/10/2024

## Criando Scripts SQL e Executando-os no Terminal
Agora que você aprendeu a utilizar comandos SQL, pode salvar uma série de instruções para realizar transações conforme sua necessidade.

Você pode usar qualquer editor de texto e salvar o arquivo com a extensão .sql. Por exemplo, vamos supor que você tenha salvo o arquivo como exemplo.sql.

Ao abrir o terminal, você pode chamar este script utilizando o comando source:

```sql
source CAMINHO_DO_ARQUIVO/exemplo.sql;
```

O MySQL executará os comandos em sequência. Tenha cuidado com os comandos utilizados no script, especialmente aqueles relacionados ao DELETE.

O vídeo abaixo é um exemplo desta aplicação:

{{< youtube id="3WlXpR2DJro" >}}


## Referências

**MySQL Tutorial.** Disponível em: <https://www.w3schools.com/mysql/default.asp>. Acesso em: 7 out. 2024.



