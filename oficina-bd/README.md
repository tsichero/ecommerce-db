## 🧰 Projeto Oficina (Módulo de Banco de Dados)
```sql
Este projeto faz parte do módulo de Modelagem de Banco de Dados, com o objetivo de aplicar as etapas de transformação do modelo conceitual (ER) para o modelo lógico relacional, implementação do banco de dados em SQL, inserção de dados de teste, e execução de consultas SQL conforme o desafio proposto.

O contexto modelado é o de uma oficina mecânica, que realiza o controle de clientes, veículos, funcionários, serviços e ordens de serviço.
Nesta pasta [`oficina-bd`](./oficina-bd) está o projeto completo de modelagem e implementação de um banco de dados relacional para o contexto de uma oficina mecânica.
```sql
Inclui:
- Modelo relacional (script SQL de criação);
- Dados de teste (inserções);
- Consultas SQL complexas;
- README explicativo.
``
```

🧱 Etapas do Projeto
```sql
Mapeamento do Esquema ER para o Modelo Relacional
Conversão das entidades e relacionamentos do modelo conceitual em tabelas relacionais, com definição de chaves primárias e estrangeiras.

Definição do Script SQL de Criação do Esquema
Criação do banco de dados e tabelas com suas restrições de integridade.

Persistência de Dados de Teste
Inserção de registros para simular o funcionamento real do sistema da oficina.

Consultas SQL Complexas
Criação de queries que utilizam as cláusulas:

SELECT

WHERE

ORDER BY

GROUP BY

HAVING

JOIN

Expressões derivadas (atributos calculados)
```

## 🗂️ Estrutura de Arquivos

oficina-bd/
├── modelo_relacional.sql     # Criação do banco e tabelas
├── dados_teste.sql           # Inserções de dados de exemplo
├── consultas.sql             # Consultas SQL complexas
└── README.md                 # Documentação do projeto
```
## 🧩 Modelo Relacional (Resumo das Tabelas)

| Tabela            | Descrição                                | Principais Atributos                          |
| ----------------- | ---------------------------------------- | --------------------------------------------- |
| **Cliente**       | Armazena informações dos clientes        | id_cliente, nome, telefone, email             |
| **Veiculo**       | Informações dos veículos dos clientes    | id_veiculo, placa, modelo, marca, ano         |
| **Funcionario**   | Funcionários da oficina                  | id_funcionario, nome, cargo, salario          |
| **Servico**       | Tipos de serviços oferecidos             | id_servico, descricao, valor                  |
| **Ordem_Servico** | Registro de ordens de serviço realizadas | id_os, data_emissao, status                   |
| **Item_Servico**  | Serviços aplicados em cada OS            | id_os, id_servico, quantidade, valor_unitario |
```

## 🧾 Exemplo de Consultas SQL
```sql
1️⃣ Consulta simples:
SELECT nome, telefone, email FROM Cliente;
2️⃣ Filtro com condição:
SELECT * FROM Ordem_Servico WHERE status = 'Em andamento';
3️⃣ Junção e cálculo:
SELECT 
    c.nome AS cliente,
    SUM(i.quantidade * i.valor_unitario) AS total_gasto
FROM Cliente c
JOIN Ordem_Servico os ON c.id_cliente = os.id_cliente
JOIN Item_Servico i ON os.id_os = i.id_os
GROUP BY c.nome
HAVING total_gasto > 300;
```
## 💾 Tecnologias Utilizadas
```sql
MySQL 8.0+

Workbench / DBeaver (para testes)

GitHub (armazenamento e versionamento)
```
## 📊 Resultados Esperados
```sql
Estrutura do banco de dados criada corretamente;

Dados de teste inseridos e funcionando;

Consultas SQL retornando resultados coerentes;

Projeto documentado e versionado no GitHub.
```
👨‍💻 Autora

Tsichero
📅 Data de conclusão: 05/11/2025
📫 Contato: [mmbjjs@gmail.com
]
