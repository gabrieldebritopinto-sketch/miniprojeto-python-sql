# 🚀 Mini-Projeto: Python + SQL (SQLite)

## 🎯 Contexto e Objetivos
Este projeto demonstra como integrar **Python** e **SQL (SQLite)** para criar, manipular e consultar dados.  
O objetivo é consolidar meus estudos e mostrar na prática como usar Python para trabalhar com bancos de dados relacionais.

---

## 📚 Curadoria de Fontes
- [Documentação oficial do Python](https://docs.python.org/3/)
- [SQLite Tutorial](https://www.sqlitetutorial.net/)
- [Pandas Documentation](https://pandas.pydata.org/docs/)
- [W3Schools SQL](https://www.w3schools.com/sql/)

---

## 🧠 Engenharia de Prompts e Cicatrizes
Durante o estudo, utilizei IA para responder perguntas estratégicas:

- **Prompt:** "Como conectar Python ao SQLite?"  
  - **Resposta:** Usando `sqlite3.connect("arquivo.db")`.  
  - **Cicatriz:** erro inicial por não fechar conexão → resolvido com `conn.close()`.

- **Prompt:** "Como ler dados SQL em Pandas?"  
  - **Resposta:** Usando `pd.read_sql_query("SELECT * FROM tabela", conn)`.  
  - **Cicatriz:** precisei instalar `pandas` manualmente com `pip install pandas`.

---

## 📒 Miniguia de Estudo

### 🔹 Resumos Estruturados
- **Python:** manipulação de listas, dicionários e DataFrames.  
- **SQL:** comandos básicos (CREATE, INSERT, SELECT, WHERE, JOIN).  
- **Integração:** uso de Python para executar queries SQL e analisar resultados com Pandas.

### 🔹 Glossário
- **Query:** instrução SQL para consultar dados.  
- **Cursor:** objeto que executa comandos SQL.  
- **DataFrame:** tabela manipulável em Pandas.  
- **Commit:** comando para salvar alterações no banco.

### 🔹 Prompts Reutilizáveis
- "Explique como usar JOIN em SQLite com exemplo prático."  
- "Mostre como carregar dados SQL em Pandas."  
- "Quais boas práticas para otimizar queries SQL?"

---

## 🧑‍💻 Exemplo de Código

```python
import sqlite3
import pandas as pd

# Criar conexão
conn = sqlite3.connect("empresa.db")
cursor = conn.cursor()

# Criar tabela
cursor.execute("""
CREATE TABLE IF NOT EXISTS funcionarios (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    nome TEXT NOT NULL,
    cargo TEXT NOT NULL,
    salario REAL
)
""")

# Inserir dados
dados = [
    ("Ana", "Analista de Dados", 4500),
    ("Bruno", "Cientista de Dados", 7000),
    ("Carla", "Engenheira de Software", 8000),
]
cursor.executemany("INSERT INTO funcionarios (nome, cargo, salario) VALUES (?, ?, ?)", dados)
conn.commit()

# Consultar dados
df = pd.read_sql_query("SELECT * FROM funcionarios", conn)
print(df)

conn.close()
