# Tarea12_SXE

## Apartado 1
``
CREATE TABLE EmpresasFCT (
    idEmpresa SERIAL PRIMARY KEY,
    nome VARCHAR(40),
    quereAlumnos BOOLEAN,
    numAlumnos INTEGER,
    fechaContacto DATE
);
``
![](https://github.com/YoelGarciaLago/Tarea12_SXE/blob/main/Captura%20desde%202025-01-30%2012-43-15.png?raw=true)

## Apartado 2
``
INSERT INTO EmpresasFCT (nome, quereAlumnos, numAlumnos, fechaContacto) VALUES
('NebulaTech Solutions', TRUE, 3, '2023-02-15'),
('EcoNova Energy', FALSE, NULL, '2023-05-01'),
('QuantumByte Systems', TRUE, 5, '2023-08-08'),
('LushBite Foods', TRUE, 2, '2024-02-28'),
('AetherSpace Travel', FALSE, NULL, '2024-06-20');
``
![](https://github.com/YoelGarciaLago/Tarea12_SXE/blob/main/Captura%20desde%202025-02-03%2009-04-38.png?raw=true)

## Apartado 3
``
 SELECT * FROM empresasfct ORDER BY fechacontacto DESC;
 ``
 ![](https://github.com/YoelGarciaLago/Tarea12_SXE/blob/main/Captura%20desde%202025-02-03%2009-09-09.png?raw=true)

 ## Apartado 4

 ``
select name, city, commercial_company_name
from res_partner where is_company = FALSE and city = 'Tracy' order by commercial_company_name asc;
 ``
 ![](https://github.com/YoelGarciaLago/Tarea12_SXE/blob/main/Captura%20desde%202025-02-03%2009-56-08.png?raw=true)

 ## Apartado 5
``
SELECT DISTINCT
    invoice_partner_display_name AS Nombre_Empresa,
    name AS Numero_Factura,
    invoice_date AS Fecha_Factura,
    amount_untaxed AS Total_Factura_Sin_Impuestos
FROM account_move
WHERE move_type = 'in_refund'
ORDER BY invoice_date DESC;
``
![](https://github.com/YoelGarciaLago/Tarea12_SXE/blob/main/Captura%20desde%202025-02-03%2009-58-41.png?raw=true)

## Apartado 6
``
SELECT 
    invoice_partner_display_name AS Nombre_Empresa,
    COUNT(DISTINCT name) AS Numero_Facturas,
    SUM(DISTINCT amount_untaxed) AS Total_Facturado_Sin_Impuestos
FROM account_move 
WHERE move_type = 'out_invoice'  
AND state = 'posted'
GROUP BY invoice_partner_display_name
HAVING COUNT(DISTINCT name) > 2;
``
![](https://github.com/YoelGarciaLago/Tarea12_SXE/blob/main/Captura%20desde%202025-02-03%2010-03-27.png?raw=true)

## Apartado 7
``
UPDATE res_partner
SET email = REPLACE(email, '@bilbao.example.com', '@bilbao.bizkaia.eus')
WHERE email LIKE '%@bilbao.example.com';
``
![](https://github.com/YoelGarciaLago/Tarea12_SXE/blob/main/Captura%20desde%202025-02-03%2010-05-36.png?raw=true)
![](https://github.com/YoelGarciaLago/Tarea12_SXE/blob/main/Captura%20desde%202025-02-03%2010-07-23.png?raw=true)

## Apartado 8
``
DELETE FROM res_partner
WHERE commercial_company_name = 'Ready Mat' 
AND is_company = FALSE;
``
![](https://github.com/YoelGarciaLago/Tarea12_SXE/blob/main/Captura%20desde%202025-02-03%2010-12-17.png?raw=true)
![](https://github.com/YoelGarciaLago/Tarea12_SXE/blob/main/Captura%20desde%202025-02-03%2010-23-09.png?raw=true)
