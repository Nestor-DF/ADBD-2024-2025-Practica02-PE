## Descripción de cada una de las entidades definidas

- **Vivero**: Representa un vivero, que es el lugar físico donde se almacenan y venden las plantas, productos de jardinería y de decoración.
- **Zona**: Representa una división dentro de un vivero, como una sección o área específica.
- **Empleado**: Persona que trabaja en el vivero y está asignado a una zona.
- **Producto**: Cualquier bien que está disponible para la venta en el vivero.
- **Pedido**: Representa una transacción en la que un cliente compra uno o varios productos.
- **Cliente**: Persona que realiza los pedidos.


## Descripción y ejemplos ilustrativos del dominio de cada uno de los atributos de las entidades y de las relaciones

1. **Código (Vivero, Zona, Producto, Empleado, Pedido, Cliente)**:
   - Descripción: Identificadores únicos de vivero, zona, producto, empleado, pedido o cliente.
   - Dominio: Un valor alfanumérico único.
   - Ejemplos:
     - Para Vivero: `V001`, `V002`.
     - Para Zona: `Z001`, `Z002`.
     - Para Producto: `P001`, `P002`.
     - Para Empleado: `E001`, `E002`.
     - Para Pedido: `PD001`, `PD002`.
     - Para Cliente: `C001`, `C002`.

2. **Nombre (Vivero, Zona, Producto, Empleado, Cliente)**:
   - Descripción: El nombre que identifica al vivero, zona, producto, empleado o cliente.
   - Dominio: Una cadena de caracteres.
   - Ejemplos:
     - Para Vivero: `"Vivero Central"`, `"Vivero Norte"`.
     - Para Zona: `"Almacén"`, `"Zona de Exposición"`.
     - Para Producto: `"Rosa Roja"`, `"Maceta de barro"`.
     - Para Empleado: `"Juan Pérez"`, `"Laura Gómez"`.
     - Para Cliente: `"Carlos Díaz"`, `"María Hernández"`.

3. **Georreferenciación (Vivero, Zona) - Atributo compuesto**:
   - Descripción: Ubicación geográfica exacta del vivero o zona, definida por latitud y longitud.
   - **Latitud**:
     - Dominio: Un número decimal entre -90 y 90.
     - Ejemplo: `28.4672`, `-16.2545`.
   - **Longitud**:
     - Dominio: Un número decimal entre -180 y 180.
     - Ejemplo: `-16.2510`, `28.4189`.

4. **Puesto (Relación Zona-Empleado)**:
   - Descripción: Cargo o rol del empleado dentro del vivero.
   - Dominio: Una cadena de texto que describe el rol del empleado.
   - Ejemplo: `"Vendedor"`, `"Encargado de Almacén"`, `"Jefe de Zona"`.

5. **Precio (Producto) - Calculado**:
   - Descripción: El valor monetario de un producto sumándole los impuestos.
   - Dominio: Un número decimal positivo.
   - Ejemplo: `15.50`, `29.99`.

6. **Stock (Relación Zona-Producto)**:
   - Descripción: Cantidad disponible del producto en la zona.
   - Dominio: Un número entero positivo.
   - Ejemplo: `100`, `50`, `200`.

7. **Importe total (Pedido)**:
   - Descripción: Suma total del precio de todos los productos en el pedido.
   - Dominio: Un número decimal positivo.
   - Ejemplo: `150.00`, `75.45`.

8. **Email (Cliente, Empleado)**:
   - Descripción: Correo electrónico del cliente o empleado.
   - Dominio: Una cadena de texto con formato de correo electrónico.
   - Ejemplo: `"empleado1@example.com"`, `"maria.hernandez@gmail.com"`.

9. **Fecha pedido (Pedido)**:
   - Descripción: Fecha en la que se realizó el pedido.
   - Dominio: Un valor de fecha en formato `DD-MM-YYYY`.
   - Ejemplo: `"12-09-2024"`, `"14-09-2024"`.

10. **Fecha ingreso (Cliente)**:
    - Descripción: Fecha en la que el cliente se hizo miembro de Tajinaste Plus.
    - Dominio: Un valor de fecha en formato `DD-MM-YYYY`.
    - Ejemplo: `"15-01-2024"`, `"10-12-2023"`.

11. **Fecha inicio/fin (Relación Zona-Empleado)**:
    - Descripción: Fecha de inicio o fin del periodo de la asignación de un empleado a una zona.
    - Dominio: Un valor de fecha en formato `DD-MM-YYYY`.
    - Ejemplo: `"15-01-2024"`, `"10-12-2023"`.
    - 
8. **Teléfono (Empleado) - Multievaluado**:
   - Descripción: Números de teléfono que tiene el empleado (Personal y de trabajo).
   - Dominio: Una cadena númerica con formato de número de teléfono.
   - Ejemplo: `622341623`, `601455267`.

## Descripción de cada una de las relaciones definidas

1. **Vivero (1,1) - (1,N) Zona**  
   Un vivero puede tener una o varias zonas. Cada zona pertenece a un único vivero, es decir, para identificar una zona es necesario conocer su vivero correspondiente.

2. **Zona (1,N) - (1,N) Producto**  
   Una zona puede contener uno o varios productos. A su vez, un producto puede estar en una o varias zonas, lo que significa que un mismo producto puede estar disponible en distintas zonas del mismo vivero o incluso en viveros diferentes.

3. **Zona (1,1) - (1,N) Empleado**  
   Cada zona tiene asignado uno o varios empleados. Sin embargo, un empleado solo puede estar asignado a una única zona donde desempeña su trabajo.

4. **Empleado (1,1) - (1,N) Pedido**  
   Un empleado puede gestionar uno o más pedidos. No obstante, cada pedido es gestionado por un solo empleado.

5. **Producto (1,N) - (1,N) Pedido**  
   Un producto puede formar parte de uno o más pedidos. A la vez, un pedido puede estar compuesto por uno o varios productos.

6. **Pedido (1,N) - (0,1) Cliente**  
   Un pedido puede estar vinculado a un cliente, pero no es obligatorio. Si el cliente no es miembro del programa Tajinaste Plus, su información no se registra, por lo que el pedido no tendría un cliente asociado.


## Restricciones semánticas que no puede recoger el modelo entidad/relación
- Un pedido no puede ser realizado si no hay productos en stock.
- El stock de un producto no puede ser negativo.
- El importe total de un pedido debe ser mayor a cero.
- El precio de un producto no puede ser negativo.
- Un empleado solo puede trabajar en una única zona durante una época específica del año, una vez terminada su asignación sí puede trabajar en una zona distinta.
- La fecha de fin de asignación de un empleado a una zona debe ser posterior a la fecha de inicio
