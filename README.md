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

---

## 🧩 Diagrama ER – E-commerce

```mermaid
erDiagram
    CLIENTE {
        int id_cliente
        string tipo_cliente
        string nome
        string cpf
        string cnpj
        string email
    }
    FORNECEDOR {
        int id_fornecedor
        string nome
        string cnpj
        string contato
    }
    VENDEDOR {
        int id_vendedor
        string nome
        string cpf
        string cnpj
        string email
    }
    PRODUTO {
        int id_produto
        string nome
        string descricao
        decimal preco
        int id_fornecedor
    }
    ESTOQUE {
        int id_estoque
        int id_produto
        int quantidade
    }
    PEDIDO {
        int id_pedido
        int id_cliente
        datetime data_pedido
        string status_pedido
        decimal valor_total
    }
    ITEM_PEDIDO {
        int id_item
        int id_pedido
        int id_produto
        int quantidade
        decimal preco_unit
    }
    PAGAMENTO {
        int id_pagamento
        int id_pedido
        string forma_pagamento
        decimal valor
    }
    ENTREGA {
        int id_entrega
        int id_pedido
        string codigo_rastreio
        string status_entrega
        datetime data_envio
    }

    CLIENTE ||--o{ PEDIDO : "faz"
    PEDIDO ||--|{ ITEM_PEDIDO : "possui"
    PRODUTO ||--o{ ITEM_PEDIDO : "vendido_em"
    FORNECEDOR ||--o{ PRODUTO : "fornece"
    PRODUTO ||--o{ ESTOQUE : "controla"
    PEDIDO ||--o{ PAGAMENTO : "gera"
    PEDIDO ||--o{ ENTREGA : "cria"
%% gráfico de barras simulando pedidos por cliente
xychart-beta
    title "Vendas por Cliente"
    x-axis "Cliente" ["Ana Souza", "Loja XPTO", "Carlos Lima"]
    y-axis "Total de Pedidos" 0 --> 10
    bar [4, 6, 3]
