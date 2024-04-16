
# Proyecto 1: Algoritmo de sistema de costos



## Planteamiento
Se requiere construir un algoritmo en pseudocódigo (PSeInt) que simule el calculo del costo de un producto con base en su precio original y el porcentaje de descuento aplicado. 

## Requerimientos

El algoritmo debe cumplir con los siguientes requisitos:
Leer el precio original del producto.
Aplicar un descuento al producto si es aplicable (por ejemplo, si el cliente tiene un cupón de descuento).
Aplicar impuestos al producto (por ejemplo, el IVA u otros impuestos).
Si el cliente compra más de un artículo, aplicar un descuento por cantidad.
Calcular el costo de envío basado en el destino y el peso del paquete.
Calcular el costo final del producto sumando el precio con descuento, impuestos, descuento por cantidad y costo de envío.
Se debe mostrar el costo final del producto, desglosando los diferentes componentes (descuentos, impuestos, descuento por cantidad y costo de envío).
En esta oportunidad el ingreso de cada valor será manual, sin asumir valores por defecto
## Explicación Paso a Paso de la solución
1. Primero, se declaran las variables en los arreglos que se utilizarán en el programa:
Primer arreglo `Definir` como `Real`:
- `precioOriginal` es la variable donde se almacenará el valor.
- `descuentoCupon` es la variable donde se almacenará el valor del cupón de descuento.
- `IVA` es un valor del impuesto IVA variable para ser ingresado por el usuario.
- `descuentoCantidad` es un valor fijo del 5% si el cliente compra más de un artículo, aplicar un descuento por cantidad por artículo adicional.
- `costoEnvio` es la variable donde se almacenará el costo de envío.
- `costoFinal` es la variable donde se almacenará el costo final que resulta del `(precioConIVA - descuentoCantidad) * cantidad + costoEnvio`


         Algoritmo CalcularCostoProducto //Nombre del Algoritmo
        Definir precioOriginal, descuentoCupon, IVA, descuentoCantidad, costoEnvio, costoFinal Como Real

2. Luego, se declaran las variables que se utilizarán en el segundo arreglo `Definir` pero ahora como `Entero`:

- `cantidad` es la variable donde se almacenará la cantidad del producto.
- `peso` es la variable donde se almacenará el peso del producto
- `indiceDestino` es un arreglo bidimensional  para almacenar los destinos y sus costos de envío.


        Definir cantidad, peso, indiceDestino Como Entero

3. A continuación, se crea un arreglo bidimensional para almacenar los destinos y sus respectivos costos de envío:

        Dimensionar destinos[5,2] Como Caracter
        destinos[1, 1] <- "Nueva York" // Nombre del destino
        destinos[1, 2] <- "16"         // Costo de envío asociado
        destinos[2, 1] <- "Miami"      // Nombre del destino
        destinos[2, 2] <- "14"         // Costo de envío asociado
        destinos[3, 1] <- "Los Angeles"// Nombre del destino
        destinos[3, 2] <- "18"         // Costo de envío asociado
        destinos[4, 1] <- "Resto de América"// Nombre del destino
        destinos[4, 2] <- "20"         // Costo de envío asociado
        destinos[5, 1] <- "Europa" // Nombre del destino
        destinos[5, 2] <- "25"     // Costo de envío asociado

4. En esta etapa del código se solicita al usuario que ingrese los datos necesarios para el cálculo:

        Escribir "Ingrese el precio original del producto:"
        Leer precioOriginal
        Escribir "Ingrese el porcentaje de descuento del cupón (sin el signo %):"
        Leer descuentoCupon
        Escribir "Ingrese el IVA aplicable (sin el signo %):"
        Leer IVA
        Escribir "Ingrese la cantidad de productos a comprar:"
        Leer cantidad
        Escribir "Ingrese el peso del paquete en kg:"
        Leer peso
    
5. En el siguiente código se muestra al usuario las opciones de destino y se solicita que elija una:

        Escribir "Seleccione el número correspondiente al destino del envío:"
        Para i <- 1 Hasta 5 Hacer
        Escribir i, ". ", destinos[i, 1]
        FinPara
        Leer indiceDestino
    
6. Convertir el costo de envío a número y asignarlo se crea la siguiente línea:

        costoEnvio <- convertirANumero(destinos[indiceDestino, 2])
    
7. A continuación se aplica el descuento del cupón al precio original:

        precioConDescuento <- precioOriginal * (1 - descuentoCupon / 100)
    
8. Calcular el precio con IVA incluido:

        precioConIVA <- precioConDescuento * (1 + IVA / 100)
    
9. Aplicar un descuento adicional si se compran más de un producto:

        Si cantidad > 1 Entonces
            descuentoCantidad <- precioConIVA * 0.05 // 5% de descuento por cantidad
        SiNo
            descuentoCantidad <- 0
        FinSi
## Código Completo
A continuación se desglosa el código completo:


    Algoritmo CalcularCostoProducto
    Definir precioOriginal, descuentoCupon, IVA, descuentoCantidad, costoEnvio, costoFinal Como Real
    Definir cantidad, peso, indiceDestino Como Entero
    Dimensionar destinos[5,2] 
    destinos[1, 1] <- "Nueva York"
    destinos[1, 2] <- "16"
    destinos[2, 1] <- "Miami"
    destinos[2, 2] <- "14"
    destinos[3, 1] <- "Los Angeles"
    destinos[3, 2] <- "18"
    destinos[4, 1] <- "Resto de América"
    destinos[4, 2] <- "20"
    destinos[5, 1] <- "Europa"
    destinos[5, 2] <- "25"
    
    Escribir "Ingrese el precio original del producto:"
    Leer precioOriginal
    Escribir "Ingrese el porcentaje de descuento del cupón (sin el signo %):"
    Leer descuentoCupon
    Escribir "Ingrese el IVA aplicable (sin el signo %):"
    Leer IVA
    Escribir "Ingrese la cantidad de productos a comprar:"
    Leer cantidad
    Escribir "Ingrese el peso del paquete en kg:"
    Leer peso
    Escribir "Seleccione el número correspondiente al destino del envío:"
    Para i <- 1 Hasta 5 Hacer
        Escribir i, ". ", destinos[i, 1]
    FinPara
    Leer indiceDestino
    
    // Convertir el costo de envío a número y asignarlo
    costoEnvio <- convertirANumero(destinos[indiceDestino, 2])
    
    // Aplicar descuento del cupón
    precioConDescuento <- precioOriginal * (1 - descuentoCupon / 100)
    
    // Aplicar IVA
    precioConIVA <- precioConDescuento * (1 + IVA / 100)
    
    // Aplicar descuento por cantidad
    Si cantidad > 1 Entonces
        descuentoCantidad <- precioConIVA * 0.05 // 5% de descuento por cantidad
    SiNo
        descuentoCantidad <- 0
    FinSi
    
    // Calcular costo final
    costoFinal <- (precioConIVA - descuentoCantidad) * cantidad + costoEnvio
    
    // Mostrar el costo final y desglose
    
    Escribir "Desglose:"
    Escribir "Precio original: $", precioOriginal
    Escribir "Descuento por cupón: $", precioOriginal * descuentoCupon / 100
    Escribir "Precio con descuento: $", precioConDescuento
    Escribir "IVA: $", precioConDescuento * IVA / 100
    Escribir "Precio con IVA: $", precioConIVA
    Escribir "Descuento por cantidad: $", descuentoCantidad
    Escribir "Precio final después del descuento por cantidad: $", precioConIVA - descuentoCantidad
    Escribir "Costo de envío para ", destinos[indiceDestino, 1], ": $", costoEnvio
	Escribir "Costo final del producto: $", costoFinal
FinAlgoritmo
