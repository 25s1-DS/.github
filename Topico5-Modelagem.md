# Estratégias de Modelagem de Dados

### 1. **Modelagem Relacional (SQL)**

**Descrição**:
Baseada em tabelas com esquemas fixos, relacionamentos via chaves primária e estrangeira. Ideal para dados normalizados e fortemente estruturados.

**Exemplo**:

```sql
Tabela Alunos(id, nome)
Tabela Cursos(id, nome)
Tabela Matriculas(aluno_id, curso_id)
```

**Mais indicada para**:

* Sistemas corporativos, financeiros, ERP, CRM, etc.
* Quando integridade e consistência dos dados são críticas.

**Vantagens**:

* ACID, SQL maduro, integridade referencial.

---

### 2. **Modelagem Documental Hierárquica (NoSQL - Schemaless)**

**Descrição**:
Dados são armazenados como documentos JSON ou BSON. A estrutura pode ser aninhada, com coleções contendo documentos com campos diversos — sem necessidade de esquema fixo.

**Exemplo** (MongoDB):

```json
{
  "nome": "João",
  "cursos": [
    {"nome": "Matemática", "nota": 9.5},
    {"nome": "Física", "nota": 8.7}
  ]
}
```

**Mais indicada para**:

* Aplicações ágeis, com mudanças frequentes na estrutura dos dados.
* APIs REST, aplicativos web e mobile.
* Situações em que leitura rápida e escalabilidade horizontal são essenciais.

**Vantagens**:

* Flexibilidade (schema dinâmico).
* Alta performance de leitura para documentos agregados.
* Ideal para estruturas hierárquicas e aninhadas.

**Ferramentas comuns**: MongoDB, CouchDB, Firebase Firestore.

---

### 3. **Modelagem em Grafo**

**Descrição**:
Representa entidades como nós e os relacionamentos como arestas. Ideal para dados com múltiplas conexões complexas.

**Exemplo**:

```plaintext
João --[é amigo de]--> Maria
João --[curtiu]--> Post123
```

**Mais indicada para**:

* Redes sociais, motores de recomendação, análise de fraudes, etc.

**Vantagens**:

* Consulta eficiente de relacionamentos complexos.
* Natural para problemas de navegação em redes.

**Ferramentas comuns**: Neo4j, Amazon Neptune, JanusGraph.

---

### 4. **Modelagem Vetorial**

**Descrição**:
Representa dados como vetores numéricos em espaços multidimensionais. Usada em IA, buscas por similaridade, NLP, imagens e geodados.

**Exemplo**:

* Vetor de texto (embedding): `[0.12, -0.45, ..., 0.89]`
* Coordenadas de localização: `(lat, lon)`

**Mais indicada para**:

* Busca semântica, recuperação de informação, recomendação.
* Geolocalização, visão computacional, IA generativa.

**Ferramentas comuns**: FAISS, Pinecone, Milvus, PostGIS (para vetores geoespaciais).

---

## Comparativo 

| Estratégia            | Estrutura                       | Melhor cenário                     | Vantagens principais                     |
| --------------------- | ------------------------------- | ---------------------------------- | ---------------------------------------- |
| **Relacional**        | Tabelas (SQL)                   | Dados fixos e normalizados         | Integridade, maturidade, padronização    |
| **Documental (JSON)** | Documentos hierárquicos (NoSQL) | Estrutura mutável, apps web/mobile | Flexível, sem esquema fixo, escalável    |
| **Grafo**             | Nós e Arestas                   | Relacionamentos complexos (redes)  | Natural para redes, performance em joins |
| **Vetorial**          | Vetores numéricos               | Similaridade, IA, geodados         | Busca por similaridade, clustering, IA   |



---


# 📘 **Tutorial 1 – Modelagem Relacional com MySQL**

### 💡 Cenário: Plataforma de ensino online

Entidades: `Alunos`, `Cursos`, `Instrutores`
Relacionamentos: `Inscrições`, `MinistradoPor`

### 🎯 Objetivo:

Modelar e criar as tabelas no MySQL com chaves primárias e estrangeiras.

### 🛠️ Passos:

1. **Criar banco de dados**

```sql
CREATE DATABASE plataforma_ensino;
USE plataforma_ensino;
```

2. **Criar tabelas principais**

```sql
CREATE TABLE Alunos (
  id INT AUTO_INCREMENT PRIMARY KEY,
  nome VARCHAR(100),
  email VARCHAR(100)
);

CREATE TABLE Cursos (
  id INT AUTO_INCREMENT PRIMARY KEY,
  titulo VARCHAR(100),
  descricao TEXT
);

CREATE TABLE Instrutores (
  id INT AUTO_INCREMENT PRIMARY KEY,
  nome VARCHAR(100),
  especialidade VARCHAR(100)
);
```

3. **Relacionamentos**

```sql
CREATE TABLE Inscricoes (
  aluno_id INT,
  curso_id INT,
  data_inscricao DATE,
  PRIMARY KEY (aluno_id, curso_id),
  FOREIGN KEY (aluno_id) REFERENCES Alunos(id),
  FOREIGN KEY (curso_id) REFERENCES Cursos(id)
);

CREATE TABLE MinistradoPor (
  instrutor_id INT,
  curso_id INT,
  PRIMARY KEY (instrutor_id, curso_id),
  FOREIGN KEY (instrutor_id) REFERENCES Instrutores(id),
  FOREIGN KEY (curso_id) REFERENCES Cursos(id)
);
```

4. **Exemplo de inserção**

```sql
INSERT INTO Alunos (nome, email) VALUES ('João', 'joao@email.com');
INSERT INTO Cursos (titulo, descricao) VALUES ('SQL Básico', 'Introdução ao SQL');
INSERT INTO Instrutores (nome, especialidade) VALUES ('Prof. Ana', 'Banco de Dados');

INSERT INTO Inscricoes (aluno_id, curso_id, data_inscricao) VALUES (1, 1, CURDATE());
INSERT INTO MinistradoPor (instrutor_id, curso_id) VALUES (1, 1);
```

---

## 📄 **Tutorial 2 – Modelagem Documental com MongoDB**

### 💡 Cenário: App de delivery

### https://www.mongodb.com/lp/cloud/atlas


Entidades: `Usuário`, `Pedido`, `Restaurante` (aninhadas)

### 🎯 Objetivo:

Modelar um documento JSON completo com subdocumentos e arrays.

### 🛠️ Exemplo com MongoDB (usando o Mongo Shell ou Compass):

```js
use deliveryApp;

db.usuarios.insertOne({
  nome: "João",
  endereco: {
    rua: "Av. Brasil",
    numero: 123,
    cidade: "Londrina"
  },
  pedidos: [
    {
      data: ISODate("2024-05-01T12:00:00Z"),
      restaurante: {
        nome: "Pizza Boa",
        categoria: "Italiana"
      },
      produtos: [
        { nome: "Pizza Margherita", preco: 40.0 },
        { nome: "Refrigerante", preco: 6.0 }
      ],
      total: 46.0
    },
    {
      data: ISODate("2024-05-02T19:30:00Z"),
      restaurante: {
        nome: "Sushi House",
        categoria: "Japonesa"
      },
      produtos: [
        { nome: "Combo Sushi", preco: 70.0 }
      ],
      total: 70.0
    }
  ]
});
```

### 📝 Dica:

Você pode consultar todos os pedidos com:

```js
db.usuarios.find({}, { nome: 1, "pedidos.data": 1, "pedidos.total": 1 });
```

---

## 🔗 **Tutorial 3 – Modelagem em Grafo com Neo4j**

### 💡 Cenário: Rede profissional

### https://neo4j.com/sandbox/

Entidades: `Usuário`, `Empresa`, `Publicação`

### 🎯 Objetivo:

Criar nós e relacionamentos usando Cypher, linguagem do Neo4j.

### 🛠️ Passos no Neo4j Browser:

1. **Criar usuários**

```cypher
CREATE (joao:Usuario {nome: "João"})
CREATE (ana:Usuario {nome: "Ana"})
```

2. **Criar empresas**

```cypher
CREATE (empresa1:Empresa {nome: "TechCorp"})
```

3. **Criar publicações**

```cypher
CREATE (pub1:Publicacao {titulo: "Meu primeiro post", data: date("2025-05-01")})
```

4. **Criar relacionamentos**

```cypher
MATCH (joao:Usuario {nome: "João"}), (ana:Usuario {nome: "Ana"})
CREATE (joao)-[:SEGUE]->(ana)

MATCH (joao:Usuario), (empresa1:Empresa)
CREATE (joao)-[:TRABALHA_EM {cargo: "Dev", desde: 2022}]->(empresa1)

MATCH (joao:Usuario), (pub1:Publicacao)
CREATE (joao)-[:PUBLICOU]->(pub1)
```

5. **Consulta exemplo** – Quem João segue?

```cypher
MATCH (joao:Usuario {nome: "João"})-[:SEGUE]->(amigo)
RETURN amigo.nome;
```

--- 
# Gran finale

1. Acessar o colab: [Data Access](./colabs/Data_access.ipynb)
   
2. Conectar o mesmo em cada um dos BDs
   
3. Integrar os dados (relacionar os dados de fontes diferentes)
   
4. Gerar gráficos para visualização

5. Gerar um PDF e submetar no AVA

