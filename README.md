 # 💻 Projeto Banco de Dados E-commerce

Projeto desenvolvido para o desafio da **DIO.me**, com o objetivo de criar um **modelo lógico e físico de banco de dados relacional** para um sistema de e-commerce.

## 📘 Descrição
O projeto representa um e-commerce completo com clientes (PF/PJ), fornecedores, produtos, pedidos, pagamentos e entregas.  
Inclui criação das tabelas, inserção de dados e consultas SQL demonstrando diferentes operações.

## 🧱 Estrutura Principal
- **cliente** – cadastro de clientes PF e PJ  
- **fornecedor** – dados dos fornecedores  
- **vendedor** – cadastro de vendedores  
- **produto** – catálogo de produtos  
- **estoque** – controle de quantidades  
- **pedido** e **item_pedido** – registros de vendas  
- **pagamento** – formas de pagamento  
- **entrega** – rastreio e status da entrega  

## 📊 Exemplos de Consultas SQL
```sql
SELECT * FROM produto WHERE preco > 200;
SELECT c.nome, COUNT(p.id_pedido) AS total_pedidos
FROM cliente c
JOIN pedido p ON c.id_cliente = p.id_cliente
GROUP BY c.nome;
🧩 Tecnologias

MySQL

SQL (DDL e DML)
