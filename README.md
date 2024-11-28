# **Guia SQL: Introdução e Principais Comandos**

## **O que é SQL?**
SQL (*Structured Query Language*) é uma linguagem usada para interagir com bancos de dados relacionais. Ela permite:
- Consultar dados.
- Modificar informações.
- Definir a estrutura do banco de dados.

---

## **1. Instruções de Consulta (DQL - Data Query Language)**  
As instruções DQL permitem consultar (ou "ler") dados do banco de dados.

- **`SELECT`**: Recupera dados de uma ou mais tabelas.  
  **Exemplo**:  
  ```sql
  SELECT nome, idade FROM clientes;
  ```

---

## **2. Instruções de Definição de Dados (DDL - Data Definition Language)**  
Comandos DDL definem a estrutura do banco de dados, como criar, alterar ou excluir tabelas.

- **`CREATE`**: Cria novos objetos no banco (tabelas, índices, etc.).  
  **Exemplo**:  
  ```sql
  CREATE TABLE clientes (
      id INT PRIMARY KEY,
      nome VARCHAR(100),
      idade INT
  );
  ```

- **`ALTER`**: Modifica a estrutura de um objeto existente.  
  **Exemplo**:  
  ```sql
  ALTER TABLE clientes ADD email VARCHAR(100);
  ```

- **`DROP`**: Exclui um objeto do banco de dados.  
  **Exemplo**:  
  ```sql
  DROP TABLE clientes;
  ```

- **`TRUNCATE`**: Remove todos os registros de uma tabela, mantendo sua estrutura.  
  **Exemplo**:  
  ```sql
  TRUNCATE TABLE clientes;
  ```

---

## **3. Instruções de Manipulação de Dados (DML - Data Manipulation Language)**  
Os comandos DML manipulam os dados dentro das tabelas.

- **`INSERT`**: Insere novos registros.  
  **Exemplo**:  
  ```sql
  INSERT INTO clientes (id, nome, idade) VALUES (1, 'João', 30);
  ```

- **`UPDATE`**: Atualiza registros existentes.  
  **Exemplo**:  
  ```sql
  UPDATE clientes SET idade = 31 WHERE id = 1;
  ```

- **`DELETE`**: Exclui registros de uma tabela.  
  **Exemplo**:  
  ```sql
  DELETE FROM clientes WHERE id = 1;
  ```

---

## **4. Instruções de Controle de Dados (DCL - Data Control Language)**  
Essas instruções controlam o acesso aos dados, concedendo ou revogando permissões.

- **`GRANT`**: Concede permissões.  
  **Exemplo**:  
  ```sql
  GRANT SELECT, INSERT ON clientes TO usuario1;
  ```

- **`REVOKE`**: Retira permissões.  
  **Exemplo**:  
  ```sql
  REVOKE SELECT, INSERT ON clientes FROM usuario1;
  ```

---

## **5. Instruções de Controle de Transações (TCL - Transaction Control Language)**  
Controlam o comportamento das transações no banco de dados.

- **`COMMIT`**: Confirma as alterações realizadas.  
  **Exemplo**:  
  ```sql
  COMMIT;
  ```

- **`ROLLBACK`**: Reverte alterações até o último `COMMIT`.  
  **Exemplo**:  
  ```sql
  ROLLBACK;
  ```

- **`SAVEPOINT`**: Define um ponto de salvamento para `ROLLBACK` parcial.  
  **Exemplo**:  
  ```sql
  SAVEPOINT ponto1;
  ```

- **`SET TRANSACTION`**: Define características da transação, como o nível de isolamento.  
  **Exemplo**:  
  ```sql
  SET TRANSACTION ISOLATION LEVEL SERIALIZABLE;
  ```

---

## **6. Comandos Adicionais**  

- **`EXPLAIN`**: Mostra o plano de execução de uma consulta para otimização.  
  **Exemplo**:  
  ```sql
  EXPLAIN SELECT * FROM clientes;
  ```

- **`WITH`**: Define *Common Table Expressions* (CTEs).  
  **Exemplo**:  
  ```sql
  WITH cte AS (
      SELECT nome, idade FROM clientes WHERE idade > 25
  )
  SELECT * FROM cte;
  ```

- **`DESCRIBE`** ou **`DESC`**: Mostra a estrutura de uma tabela.  
  **Exemplo**:  
  ```sql
  DESCRIBE clientes;
  ```

---

## **Modelo Relacional de Dados**

### **Componentes Principais**:
1. **Tabelas**: Estruturas que armazenam os dados (linhas e colunas).  
2. **Chaves**:
   - **Primária (PK)**: Identifica de forma única cada registro.  
   - **Estrangeira (FK)**: Cria relacionamentos entre tabelas.  
3. **Normalização**: Organização de dados para minimizar redundâncias.

---

## **Boas Práticas com SQL**

- **Evite `SELECT *`**: Consulte apenas as colunas necessárias.  
- **Use índices com cautela**: Eles aceleram consultas, mas podem impactar operações de escrita.  
- **Otimize *JOINs***: Certifique-se de que as tabelas possuem índices adequados.  
- **Cuidado com subconsultas complexas**: Prefira reestruturar consultas usando *JOINs* ou *CTEs*.

---

## **Bancos de Dados Não Relacionais (NoSQL)**

### **Características**:
- Escalabilidade horizontal.  
- Modelos de dados flexíveis.  
- Alta disponibilidade.

### **Tipos de NoSQL**:
1. **Chave-Valor**: Ex.: Redis, Riak.  
   **Exemplo**:  
   ```redis
   SET user:1 "João"
   GET user:1
   ```

2. **Documentos**: Ex.: MongoDB, CouchDB.  
   **Exemplo**:  
   ```json
   {
       "_id": "1",
       "nome": "João",
       "idade": 30
   }
   ```

3. **Colunas**: Ex.: Cassandra, HBase.  
   **Exemplo**:  
   ```sql
   CREATE TABLE clientes (
       id UUID PRIMARY KEY,
       nome TEXT,
       idade INT
   );
   ```
