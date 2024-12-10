CREATE TABLE Clientes (
    id_cliente INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(255),
    telefone VARCHAR(20),
    tipo_cliente ENUM('PF', 'PJ') NOT NULL,
    cpf_cnpj VARCHAR(14) UNIQUE
);

CREATE TABLE Produtos (
    id_produto INT PRIMARY KEY AUTO_INCREMENT,
    nome_produto VARCHAR(255),
    descricao TEXT,
    preco DECIMAL(10, 2)
);

CREATE TABLE Pedidos (
    id_pedido INT PRIMARY KEY AUTO_INCREMENT,
    id_cliente INT,
    data_pedido DATE,
    status_pedido ENUM('Pendente', 'Pago', 'Cancelado'),
    total DECIMAL(10, 2),
    FOREIGN KEY (id_cliente) REFERENCES Clientes(id_cliente)
);

INSERT INTO Clientes (nome, telefone, tipo_cliente, cpf_cnpj) 
VALUES ('João Silva', '11999999999', 'PF', '12345678901');

INSERT INTO Produtos (nome_produto, descricao, preco) 
VALUES ('Notebook', 'Notebook de alta performance', 3500.00);

INSERT INTO Pedidos (id_cliente, data_pedido, status_pedido, total) 
VALUES (1, '2024-12-01', 'Pago', 3500.00);
