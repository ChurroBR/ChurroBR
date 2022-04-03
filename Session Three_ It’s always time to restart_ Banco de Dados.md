# Session Three: It's always time to restart/ Banco de Dados

autor: Nilton da Silva Moreira
turma: Info - A
numero: 

## Criar as tabelas respeitando os relacionamentos do DER.

![](https://i.imgur.com/w0v8wiY.jpg)


## Inserir uma massa de dados que contenha no mínimo:

### ▪ 20 produtos e seus respectivos estoque;


```sql=
CREATE TABLE TB_CATEGORIA (
   ID_CATEGORIA 	INT PRIMARY KEY AUTO_INCREMENT,
   NM_CATEGORIA	VARCHAR (255)
 );
   
   
 CREATE TABLE TB_PRODUTO (
   ID_PRODUTO 		INT PRIMARY KEY AUTO_INCREMENT,
   ID_CATEGORIA	INT,
   NM_PRODUTO		VARCHAR (255),
   VL_PRECO		DECIMAL (15,2),
   FOREIGN KEY (ID_CATEGORIA)
   REFERENCES TB_CATEGORIA (ID_CATEGORIA)
   ON DELETE CASCADE
  );
   
   
 CREATE TABLE TB_ESTOQUE(
   ID_ESTOQUE		INT PRIMARY KEY AUTO_INCREMENT,
   ID_PRODUTO		INT,
   QTD_MINIMA		INT,
   QTD_DISPONIVEL	INT,
   FOREIGN KEY (ID_PRODUTO)
   REFERENCES TB_PRODUTO (ID_PRODUTO)
   ON DELETE CASCADE
);

 CREATE TABLE TB_ENDERECO(
   ID_ENDERECO 	INT PRIMARY KEY AUTO_INCREMENT,
   DS_CEP		VARCHAR (255),
   DS_ENDERECO		VARCHAR (255),
   NR_ENDERECO		VARCHAR (255),
   DS_CIDADE		VARCHAR (255)
 );
 
 CREATE TABLE TB_CLIENTE (
   ID_CLIENTE		INT PRIMARY KEY AUTO_INCREMENT,
   NM_CLIENTE		VARCHAR (255),	
   DS_CPF		VARCHAR (255),
   ID_ENDERECO		INT,
   FOREIGN KEY (ID_ENDERECO)
   REFERENCES TB_ENDERECO (ID_ENDERECO) 
   ON DELETE CASCADE
  );
  
  CREATE TABLE TB_VENDA (
    ID_VENDA 		INT PRIMARY KEY AUTO_INCREMENT,
    ID_CLIENTE		INT,
    DS_NOTA_FISCAL	VARCHAR (255),
    TP_FORMA_PAGTO	VARCHAR (255),
    QTD_PARCELAS	INT,
    DT_VENDA		DATETIME,
    ID_ENDERECO 	INT,
    FOREIGN KEY (ID_CLIENTE)
    REFERENCES TB_CLIENTE (ID_CLIENTE) 
    ON DELETE CASCADE,
    
    FOREIGN KEY (ID_ENDERECO)
    REFERENCES TB_ENDERECO (ID_ENDERECO) 
    ON DELETE CASCADE
  );
   
 CREATE TABLE TB_VENDA_ITEM (
   ID_VENDA_ITEM	INT PRIMARY KEY AUTO_INCREMENT,
   ID_VENDA		INT,
   ID_PRODUTO		INT,
   FOREIGN KEY (ID_VENDA)
    REFERENCES TB_VENDA (ID_VENDA) 
    ON DELETE CASCADE,
    
    FOREIGN KEY (ID_PRODUTO)
    REFERENCES TB_PRODUTO (ID_PRODUTO) 
    ON DELETE CASCADE
);
```
## ▪ 25 clientes

```sql=
INSERT INTO TB_CATEGORIA (NM_CATEGORIA)
VALUES  ('FEMININO'),
        ('MASCULINO'),
        ('INFANTIL'),
        ('UNISSEX');
        
INSERT INTO TB_PRODUTO (ID_CATEGORIA, NM_PRODUTO, VL_PRECO)
VALUES (1, 'CALÇA JEANS', 85.90),
	(1, 'CROPPED', 39.90),
        (1, 'VESTIDO', 99.90),
        (1, 'BLUSA DE MOLETOM', 105.90),
        (1, 'SHORT JEANS', 69.90),
        (2, 'JAQUETA DE COURO', 150.00),
        (2, 'CAMISETA', 26.70),
        (2,'REGATA', 20.90),
        (2, 'CALÇA JEANS', 89.90),
        (2, 'SHORT DE MOLETOM', 110.00),
        (3, 'BODY', 59.90),
        (3, 'SAIA', 25.90),
        (3, 'MACACÃO', 89.80),
        (3, 'VESTIDO', 53.40),
        (3, 'CAMISA', 20.00),
        (4, 'BLAZER', 209.99),
        (4, 'CALÇA DE MOLETOM', 100.00),
        (4, 'CAMISETA', 45.50),
        (4, 'MEIA PERSONALIZADA', 19.90),
        (4, 'JAQUETA JEANS', 129.99);
        
 INSERT INTO TB_ESTOQUE (ID_PRODUTO, QTD_MINIMA, QTD_DISPONIVEL)
 VALUES (1, 10, 25),
 	(2, 15, 45),
        (3, 10, 15),
        (4, 5, 6),
        (5, 10, 13),
        (6, 5, 26),
        (7, 15, 45),
        (8, 10, 67),
        (9, 10, 85),
        (10, 5, 34),
        (11,  9, 23),
        (12, 4, 10),
        (13, 10, 59),
        (14, 12, 13),
        (15, 2, 9),
        (16, 5, 2),
        (17, 8, 47),
        (18, 10, 102),
        (19, 10, 39),
        (20, 5, 55);
```

## ▪ 50 vendas com items variados

```sql=
INSERT INTO TB_VENDA (ID_CLIENTE, DS_NOTA_FISCAL, TP_FORMA_PAGTO, QTD_PARCELAS, DT_VENDA, ID_ENDERECO)
 VALUES (1, '00215', 'CARTÃO', 3, '2021-05-10', 1),
 	(2, '00321', 'DINHEIRO', 0, '2021-05-10', 4),
        (3, '00369', 'DINHEIRO', 0, '2021-05-10', 6),
        (3, '00389', 'CARTÃO', 2, '2021-05-15', 6),
        (4, '00397', 'CARTÃO', 1, '2021-05-15', 10),
        (5, '00412', 'DINHEIRO', 0, '2021-05-15', 2),
        (6, '00419', 'DINHEIRO', 0, '2021-05-15', 3),
        (7, '00422', 'CARTÃO', 1, '2021-05-16', 5),
        (8, '00428', 'CARTÃO', 2, '2021-05-16', 7),
        (9, '00434', 'CARTÃO', 1, '2021-05-16', 8),
        (10,'00438', 'DINHEIRO', 0, '2021-05-16',9),
        (10,'00441', 'CARTÃO', 2, '2021-05-17', 9),
        (11,'00448', 'DINHEIRO', 0, '2021-05-17', 11),
        (12,'00502', 'DINHEIRO', 0, '2021-05-17', 1),
        (13,'00511', 'CARTÃO', 2, '2021-05-18', 14),
        (14,'00516', 'CARTÃO', 1, '2021-05-18', 16),
        (14,'00519', 'CARTÃO', 1, '2021-05-19', 16),
        (15,'00524', 'DINHEIRO', 0, '2021-05-19', 19),
        (16,'00528', 'DINHEIRO', 0, '2021-05-19', 22),
        (17,'00555', 'DINHEIRO', 0, '2021-05-19', 21),
        (18,'00559', 'CARTÃO', 2, '2021-05-20', 18),
        (19,'00563', 'CARTÃO', 1, '2021-05-20', 15),
        (20,'00567', 'DINHEIRO', 0, '2021-05-20', 12),
        (21,'00578', 'DINHEIRO', 0, '2021-05-20', 20),
        (22,'00579', 'DINHEIRO', 0, '2021-05-21', 9),
        (23,'00581', 'DINHEIRO', 0, '2021-05-21', 13),
        (24,'00585', 'CARTÃO', 1, '2021-05-21', 17),
        (25,'00592', 'CARTÃO', 3, '2021-05-21', 6),
        (25,'00598', 'DINHEIRO', 0, '2021-05-21', 6),
        (7,'00601', 'CARTÃO', 1, '2021-05-22', 5),
        (2,'00612', 'CARTÃO', 2, '2021-05-22', 4),
        (3,'00626', 'DINHEIRO', 0, '2021-05-22', 6),
        (4,'00634', 'DINHEIRO', 0, '2021-05-22', 10),
        (5,'00638', 'CARTÃO', 2, '2021-05-23', 2),
        (6,'00655', 'CARTÃO', 6,'2021-05-23', 3),
        (7,'00678', 'DINHEIRO', 0, '2021-05-23', 5),
        (8,'00684', 'DINHEIRO', 0, '2021-05-24', 7),
        (9,'00699', 'CARTÃO', 1, '2021-05-24', 8),
        (10,'00701', 'CARTÃO', 1, '2021-05-24', 9),
        (11,'00715', 'DINHEIRO', 0, '2021-05-25', 11),
        (12,'00723', 'DINHEIRO', 0, '2021-05-25', 1),
        (14,'00758', 'CARTÃO', 1, '2021-05-25', 16),
        (17,'00798', 'DINHEIRO', 0, '2021-05-26', 21),
        (20,'00805', 'DINHEIRO', 0, '2021-05-26',12),
        (21,'00812', 'DINHEIRO', 0, '2021-05-26', 20),
        (22,'00816', 'CARTÃO', 2, '2021-05-27', 9),
        (1, '00817', 'CARTÃO', 1, '2021-05-27', 1),
        (5, '00826', 'DINHEIRO', 0, '2021-05-27', 2),
        (23,'00831', 'DINHEIRO', 0, '2021-05-28', 13),
        (3, '00845', 'DINHEIRO', 0, '2021-05-28', 6);
        
  INSERT INTO TB_VENDA_ITEM (ID_VENDA, ID_PRODUTO)
  VALUES (1, 2),
  	    (1, 1),
            (2, 6),
            (3, 15),
            (3, 1),
            (4, 10),
            (4, 13),
            (5, 1),
            (6, 15),
            (7, 20),
            (8, 19),
            (8, 10),
            (9, 2),
            (9, 8),
            (10, 1),
            (11, 9),
            (11, 14),
            (12, 17),
            (13, 2),
            (13, 5),
            (14, 20),
            (15, 4),
            (16, 5),
            (16, 2),
            (17, 16),
            (18, 1),
            (19, 8),
            (20, 9),
            (21, 7),
            (22, 7),
            (23, 2),
            (24, 12),
            (25, 10),
            (25, 14),
            (26, 6),
            (27, 1),
            (27, 13),
            (28, 5),
            (29, 1),
            (29, 8),
            (30, 11),
            (31, 16),
            (32, 9),
            (33, 5),
            (34, 7),
            (34, 2),
            (35, 14),
            (36, 18),
            (37,  6),
            (38, 15),
            (39, 3),
            (40, 3),
            (41, 1),
            (42, 3),
            (43, 10),
            (44, 2),
            (45, 7),
            (46, 20),
            (47, 6),
            (48, 4),
            (48, 16),
            (49, 17),
            (50, 13),
            (50, 8),
            (50, 9);
```