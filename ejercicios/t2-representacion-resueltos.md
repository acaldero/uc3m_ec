## Materiales para Estructura de Computadores

<html>
<h2><ul>
<li>License <a href="http:/creativecommons.org/licenses/by-nc/4.0/">CC BY-NC 4.0</a> </li>
<li>Curso 2022-2023</li>
</ul></h2>
</html>


### Ejercicio 1

   (enunciado) Los siguientes números usan la representación de complemento a dos con 6 bits.
   Indique el correspondiente valor decimal:
   * 100000
   * 010011
    
   (solución) El valor decimal correspondiente:
   * 100000: - (011111 + 1) = -32 
   * 010011: +16+2+1 = 19

### Ejercicio 2

   (enunciado)
<html>
Un computador tiene un ancho de palabra que permite representar números en complemento a dos en el rango de [-234, 234-1].
Responda a las siguientes preguntas:
<ol type="a">
  <li>¿Cuál es el ancho de palabra en el computador?</li>
  <li>¿Cuántos KiB de memoria pueden direccionarse como mucho en el computador?</li>
</ol>
</html>

   (solución)
<html>
Para este computador:
<ol type="a">
  <li>[2<sup>n-1</sup>...-1, 0... 2<sup>n-1</sup>-1] = [-234, 234-1] -> 2<sup>n-1</sup>=234 -> 9 bits</li>
  <li>Si es un computador de 9 bits entonces 2<sup>9</sup> bytes (memoria direccionada por bytes) -> 2<sup>9</sup>/2<sup>10</sup> KiB -> medio kilobyte</li>
</ol>
</html>

### Ejercicio 3

   (enunciado) Indique el valor decimal correspondiente a los siguientes números codificados en el estándar IEEE 754 de simple precisión: 0xBF400000, 0x7F804000 y 0x00180000.

   (solución)
   * 0xBF400000 -> 1011 1111 0100 0000 0000... -> 1 01111110 100000000... -> -1.1 * 2<sup>-1</sup> -> 0,110 -> -0,75
   * 0x7F804000 -> 0111 1111 1000 0000 0100... -> 0 11111111 000000001... -> NaN
   * 0x00180000 -> 0000 0000 0001 0100 0000... -> 0 00000000 001010000... -> no-normalize: +0.001100.. x 2<sup>-126</sup>

### Ejercicio 4

   (enunciado) Represente en simple precisión usando IEEE 754 los números 15 y 3.75
    
   (solución) El valor decimal correspondiente:
   * 15   -> 8+4+2+1      -> 1111.00 * 2^0 -> 1.1110 * 2^3 -> 0 10000010 111000...
   * 3.75 -> 2+1+0.5+0.25 ->   11.11 * 2^0 -> 1.1110 * 2^1 -> 0 10000000 111000...

### Ejercicio 5

   (enunciado) Sume los números anteriores usando la representación IEEE 754.

   (solución) Los valores correspondientes son:
```
                                 1 11
   * 15    <-> 1,1110 * 2^3 <->  1,111000 * 2^3
   *  3,75 <-> 1,1110 * 2^1 <->  0,011110 * 2^3
   * 18,75                      10,010110 * 2^3 -> 10010,11
```

