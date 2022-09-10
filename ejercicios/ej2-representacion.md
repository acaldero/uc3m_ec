## Materiales usados bajo licencia [CC BY-NC 4.0](http://creativecommons.org/licenses/by-nc/4.0/)

## Estructura de Computadores (2022-2023)

### Ejercicio 1

   (enunciado) Los siguientes números usan la representación de complemento a dos con 6 bits.
   Indique el correspondiente valor decimal:
   * 100000
   * 010011
    
   (solución) El valor decimal correspondiente:
   * 100000: - (011111 + 1) = -32 
   * 010011: +16+2+1 = 19

### Ejercicio 2

   (enunciado) Represente en simple precisión usando IEEE 754 los números 15 y 3.75
    
   (solución) El valor decimal correspondiente:
   * 15   -> 8+4+2+1      -> 1111.00 * 2^0 -> 1.1110 * 2^3 -> 0 10000010 111000...
   * 3.75 -> 2+1+0.5+0.25 ->   11.11 * 2^0 -> 1.1110 * 2^1 -> 0 10000000 111000...

### Ejercicio 3

   (enunciado) Indique el valor decimal correspondiente al siguiente número codificado en el estándar IEEE 754 de simple precisión: 0xBF400000

   (solución) 0xBF400000 -> 1011 1111 0100 0000... -> 1 01111110 100000... -> -1.1 * 2^(-1) -> 0,110 -> -0,75

