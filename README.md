
# Proyecto 1: Algoritmo de sistema de costos

images/banner.png


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
1. Primero, se declaran las variables que se utilizarán en el programa:

- `precioOriginal` es la variable donde se almacenará el valor.
- `descuentoCupon` es la variable donde se almacenará el valor del cupón de descuento
- `descuentoCantidad` es un arreglo unidimensional de cadenas que almacenará los resultados de las materias (aprobado o reprobado).
- `costoEnvio` es la variable donde se almacenará el costo de envío.


        Algoritmo CalcularCostoProducto //Nombre del Algoritmo
            Definir precioOriginal, descuentoCupon, descuentoCantidad, costoEnvio, costoFinal Como Real
            Definir cantidad, peso, costoFijoEnvio, costoPorKg Como Entero
## Código Completo
A continuación se desglosa el código completo:


    Algoritmo CalcularCostoProducto
    Definir precioOriginal, descuentoCupon, descuentoCantidad, costoEnvio, costoFinal Como Real
    Definir cantidad, peso, costoFijoEnvio, costoPorKg Como Entero
    
    
    Escribir "Ingrese el precio original:"
    Leer precioOriginal
    Escribir "Ingrese el descuento del cupón (%):"
    Leer descuentoCupon
    Escribir "Ingrese la cantidad de productos:"
    Leer cantidad
    Escribir "Ingrese el peso del paquete (kg):"
    Leer peso
    Escribir "Ingrese el costo fijo de envío:"
    Leer costoFijoEnvio
    Escribir "Ingrese el costo por kg para el envío:"
    Leer costoPorKg
    
    
    precioConDescuento <- precioOriginal - (precioOriginal * descuentoCupon / 100)
    
    
    precioConIVA <- precioConDescuento * 1.12
    
    Si cantidad > 1 Entonces
        Escribir "Ingrese el descuento por cantidad (%):"
        Leer descuentoCantidad
        precioConDescuentoCantidad <- precioConIVA * (1 - descuentoCantidad / 100)
    SiNo
        precioConDescuentoCantidad <- precioConIVA
    FinSi
    
    costoEnvio <- costoFijoEnvio + (peso * costoPorKg)
    

    costoFinal <- (precioConDescuentoCantidad * cantidad) + costoEnvio
    
    Escribir "Costo final del producto: $", costoFinal
    Escribir "Desglose:"
    Escribir "Precio original: $", precioOriginal
    Escribir "Descuento por cupón: $", precioOriginal * descuentoCupon / 100
    Escribir "Precio con descuento: $", precioConDescuento
    Escribir "IVA: $", precioConDescuento * 0.19
    Escribir "Precio con IVA: $", precioConIVA
    Escribir "Descuento por cantidad: $", precioConIVA * descuentoCantidad / 100
    Escribir "Precio con descuento por cantidad: $", precioConDescuentoCantidad
    Escribir "Costo de envío: $", costoEnvio
FinAlgoritmo
