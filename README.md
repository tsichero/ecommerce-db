# 💻 Projeto Banco de Dados E-commerce

Projeto desenvolvido para o desafio da **DIO.me**, com o objetivo de criar um **modelo lógico e físico de banco de dados relacional** para um sistema de e-commerce.

________________________________________

## 📘 Descrição

Este projeto representa um e-commerce completo com clientes (PF/PJ), fornecedores, produtos, pedidos, pagamentos e entregas.  
Inclui criação das tabelas, inserção de dados e consultas SQL demonstrando diferentes operações.

________________________________________

## 🧱 Estrutura Principal

- **cliente** – cadastro de clientes PF e PJ  
- **fornecedor** – dados dos fornecedores  
- **vendedor** – cadastro de vendedores  
- **produto** – catálogo de produtos  
- **estoque** – controle de quantidades  
- **pedido** e **item_pedido** – registros de vendas  
- **pagamento** – formas de pagamento  
- **entrega** – rastreio e status da entrega  

________________________________________

## 📊 Exemplos de Consultas SQL

```sql
-- Produtos com preço acima de 200
SELECT * FROM produto WHERE preco > 200;

-- Total de pedidos por cliente
SELECT c.nome, COUNT(p.id_pedido) AS total_pedidos
FROM cliente c
JOIN pedido p ON c.id_cliente = p.id_cliente
GROUP BY c.nome;
```

________________________________________

## 🛠 Tecnologias
```sql
🗄️ MySQL – banco de dados relacional
💻 SQL (DDL e DML) – definição e manipulação de tabelas
📝 Markdown – documentação do projeto
📊 Mermaid (opcional) – diagramas ER visualizados no GitHub
```  
________________________________________

## 🧩 Diagrama ER – E-commerce (Texto Puro)
```sql
CLIENTE
├─ id_cliente (PK)
├─ tipo_cliente
├─ nome
├─ cpf
├─ cnpj
└─ email
│
└───<realiza> PEDIDO
├─ id_pedido (PK)
├─ id_cliente (FK)
├─ data_pedido
├─ status_pedido
└─ valor_total
│
├───<contém> ITEM_PEDIDO
│ ├─ id_item (PK)
│ ├─ id_pedido (FK)
│ ├─ id_produto (FK)
│ ├─ quantidade
│ └─ preco_unit
│
├───<gera> PAGAMENTO
│ ├─ id_pagamento (PK)
│ ├─ id_pedido (FK)
│ ├─ forma_pagamento
│ └─ valor
│
└───<gera> ENTREGA
├─ id_entrega (PK)
├─ id_pedido (FK)
├─ codigo_rastreio
├─ status_entrega
└─ data_envio

PRODUTO
├─ id_produto (PK)
├─ nome
├─ descricao
├─ preco
├─ id_fornecedor (FK)
│
└───<vendido_em> ITEM_PEDIDO
│
└───<controla> ESTOQUE
├─ id_estoque (PK)
├─ id_produto (FK)
└─ quantidade

FORNECEDOR
├─ id_fornecedor (PK)
├─ nome
├─ cnpj
└─ contato
│
└───<fornece> PRODUTO

VENDEDOR
├─ id_vendedor (PK)
├─ nome
├─ cpf
├─ cnpj
└─ email
```
________________________________________

## 📊 Gráficos de Vendas (Dashboard Visual)
```sql
Visualização das vendas por cliente, produto e faturamento mensal usando barras proporcionais (▓).

👥 Vendas por Cliente
Ana Souza                  ▓▓▓▓       4
Loja XPTO                  ▓▓▓▓▓▓     6
Carlos Lima                ▓▓▓        3

🛒 Vendas por Produto
Camiseta Azul              ▓▓▓▓       4
Tênis Esportivo            ▓▓▓▓▓      5
Mochila Verde              ▓▓         2

💰 Faturamento Mensal
Janeiro                    ▓▓▓▓▓      5000
Fevereiro                  ▓▓▓▓       4000
Março                      ▓▓▓▓▓▓     6000

```
________________________________________

## 🚀 Como Rodar / Testar o Projeto
```sql
1️⃣ Clone este repositório:  
   git clone https://github.com/seu-usuario/projeto-ecommerce.git  

2️⃣ Acesse a pasta do projeto:  
   cd projeto-ecommerce  

3️⃣ Abra o MySQL ou qualquer cliente de banco de dados compatível.  

4️⃣ Crie o banco de dados:  
   CREATE DATABASE ecommerce;  

5️⃣ Execute os scripts SQL para criar as tabelas e inserir dados:  
   source scripts/criar_tabelas.sql;  
   source scripts/inserir_dados.sql;  

6️⃣ Execute consultas de exemplo:  
   SELECT * FROM produto WHERE preco > 200;  
   SELECT c.nome, COUNT(p.id_pedido) AS total_pedidos
   FROM cliente c
   JOIN pedido p ON c.id_cliente = p.id_cliente
   GROUP BY c.nome;
```
________________________________________

📈 Exemplos Avançados de Queries
```sql
-- Top 5 produtos mais vendidos
SELECT p.nome, SUM(i.quantidade) AS total_vendido
FROM produto p
JOIN item_pedido i ON p.id_produto = i.id_produto
GROUP BY p.nome
ORDER BY total_vendido DESC
LIMIT 5;

-- Faturamento por cliente
SELECT c.nome, SUM(p.valor_total) AS faturamento
FROM cliente c
JOIN pedido p ON c.id_cliente = p.id_cliente
GROUP BY c.nome
ORDER BY faturamento DESC;

-- Estoque baixo (menos de 5 unidades)
SELECT p.nome, e.quantidade
FROM produto p
JOIN estoque e ON p.id_produto = e.id_produto
WHERE e.quantidade < 5;
```
________________________________________

## 👤 Autora

Este projeto foi desenvolvido por **Tsichero** – [GitHub](https://github.com/tsichero)
