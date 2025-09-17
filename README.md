#COM ESSE CODIGO, VOCÊ CRIA SUA TABELA !


CREATE TABLE clientes (
    id_cliente INTEGER PRIMARY KEY AUTOINCREMENT,
    nome TEXT NOT NULL
);

CREATE TABLE produtos (
    id_produto INTEGER PRIMARY KEY AUTOINCREMENT,
    nome TEXT NOT NULL,
    preco REAL NOT NULL
);

CREATE TABLE pagamento (
    id_pagamento INTEGER PRIMARY KEY AUTOINCREMENT,
    forma_pagamento TEXT NOT NULL
);

CREATE TABLE pedidos (
    id_pedido INTEGER PRIMARY KEY AUTOINCREMENT,
    id_cliente INTEGER NOT NULL,
    id_produto INTEGER NOT NULL,
    id_pagamento INTEGER NOT NULL,
    quantidade INTEGER NOT NULL,
    data_pedido TEXT NOT NULL,
    FOREIGN KEY (id_cliente) REFERENCES clientes(id_cliente),
    FOREIGN KEY (id_produto) REFERENCES produtos(id_produto),
    FOREIGN KEY (id_pagamento) REFERENCES pagamento(id_pagamento)
);



#ESSE CODIGO, SERVE PARA ADICIONAR OS DADOS NA TABELA !

Clientes
INSERT INTO clientes (nome) VALUES
('Victor'),
('RICARDO'),
('João');

-- Produtos
INSERT INTO produtos (nome, preco) VALUES
('PNEU_VIRTUS', 49.90),
('CARTEIRA', 199.90),
('BONÉ', 39.90),
('CALÇA', 129.90),
('JAQUETA', 249.90);

-- Pagamento
INSERT INTO pagamento (forma_pagamento) VALUES
('Cartão de Crédito'),
('Pix'),
('Dinheiro');

-- Pedidos
INSERT INTO pedidos (id_cliente, id_produto, id_pagamento, quantidade, data_pedido) VALUES
(1, 1, 1, 2, '2025-09-17'),
(2, 3, 2, 1, '2025-09-16'),




# ESSE CODIGO, SERVE PARA JUNTAR OU RENOMEAR UNIR TODAS AS TABELAS !

SELECT
    pedidos.id_pedido,
    clientes.nome AS nome_cliente,
    produtos.nome AS nome_produto,
    produtos.preco,
    pedidos.quantidade,
    pedidos.data_pedido,
    pagamento.forma_pagamento
FROM pedidos
JOIN clientes ON pedidos.id_cliente = clientes.id_cliente
JOIN produtos ON pedidos.id_produto = produtos.id_produto
JOIN pagamento ON pedidos.id_pagamento = pagamento.id_pagamento
ORDER BY pedidos.id_pedido;
(3, 2, 3, 5, '2025-09-15'),
(1, 4, 1, 3, '2025-09-14'),
(2, 5, 2, 10, '2025-09-13');
