## Materiales para Estructura de Computadores

<html>
<h2><ul>
<li>License <a href="http:/creativecommons.org/licenses/by-nc/4.0/">CC BY-NC 4.0</a> </li>
<li>Curso 2022-2023</li>
</ul></h2>
</html>


### Ejercicio 1

   (enunciado)
<html>
Sea un computador de 20 bits con memoria virtual paginada con páginas de 1 KiB y un total de memoria física de 512 KB.<br>
Se pide, de forma razonada y breve:<br>
<ol type="a">
<li>¿Cuál es el formato de la dirección virtual? Indique los campos y el número de bits de los mismos.</li>
<li>¿Cuál es el número máximo de entradas de la tabla de páginas (de un nivel)? </li>
<li>¿Cuántos marcos de página tiene la memoria principal? </li>
<li>¿Cuáles son los campos que se incluyen en una entrada de la tabla de páginas? Indique también para qué se utiliza cada uno de los campos. </li>
</ol>
</html>

   (solución)
<html>
<ol type="a">
<li>Las páginas ocupan 1 KB = 2<sup>10</sup> bytes. Como la dirección virtual ocupa 20 bits, se emplean 20 - 10 = 10 bits para el número de página. Por tanto, el formato emplea los 10 bits superiores de la dirección para representar el número de página y los 10 bits inferiores para representar el desplazamiento dentro de la página.</li>
<li>El número máximo de entradas de la tabla de páginas coincide con el número máximo de páginas, es decir 2<sup>10</sup> = 1024 entradas.</li>
<li>El número de marcos de página viene dado por 512 KB / 1 KB = 512 marcos.</li>
<li>En cada entrada de la tabla de página se incluye, entre otros:
<ul>
<li>Bit de presencia</li>
<li>Bit de modificado</li>
<li>Bit de validez</li>
<li>Campo en el que se almacena el marco</li>
</ul>
</ol>
</html>

