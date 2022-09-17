## Materiales para Estructura de Computadores

<html>
<h2><ul>
<li>License <a href="http:/creativecommons.org/licenses/by-nc/4.0/">CC BY-NC 4.0</a> </li>
<li>Curso 2022-2023</li>
</ul></h2>
</html>


### Ejercicio 1

   (enunciado) Convierta el siguiente número binario de 16 bits a hexadecimal: 1101001011101011
    
   (solución) 1101001011101010 -> 1101 0010 1110 1011 -> 0xD2EB

### Ejercicio 2

   (enunciado) Convierta el siguiente número hexadecimal a binario: F73AB592

   (solución) F73AB592 -> 1111 0111 0011 1010 1011 0101 1001 0010

### Ejercicio 3

   (enunciado)
<html>
Considere un computador hipotético con un ancho de palabra de 24 bits con 55 registros que direcciona una memoria a nivel de bytes.<br>
Responda a las siguientes preguntas:<br>
<ol type="a">
  <li>¿Cuántos bits se usan para el direccionamiento de la memoria?</li>
  <li>¿Cuál es el tamaño de los registros?</li>
  <li>¿Cuántos bits se almacenan en cada celda de memoria?</li>
  <li>¿Cuántas posiciones de memoria se pueden direccionar?. Exprese el resultado en KiB</li>
  <li>¿Cuántos bits se necesitan para identificar un registro?</li>
</ol>
</html>

   (solución)
<html>
<ol type="a">
  <li>Se usan 24 bits (el ancho de palabra del computador si no se indica en el enunciado una información particular al respecto).</li>
  <li>Se usan 24 bits (el ancho de palabra del computador si no se indica en el enunciado una información particular al respecto).</li>
  <li>En cada posición se almacena un byte porque es una memoria direccionable a nivel de byte.</li>
  <li>Se puede direccionar 2^24 posiciones de memoria. En cada posición se almacena un byte.</li>
  <li>Dado que hay 55 registros, se precisa redonde_exceso(ln2(55)) = 6 bits.</li>
</ol>
</html>

