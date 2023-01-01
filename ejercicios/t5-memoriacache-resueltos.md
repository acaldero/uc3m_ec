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
Sea un computador con las siguientes características:<br>
<ul>
<li>Tiempo de acceso a bloque de MP: 150 ns.</li>
<li>Tiempo de acceso a caché: 5 ns.</li>
</ul>

Se pide, de forma razonada y breve:<br>
<ol type="a">
<li>Con una tasa de aciertos del 90% en la caché. ¿Cuál es el tiempo medio de acceso a memoria ahora?</li>
<li>Si se necesita que el tiempo medio de acceso sea menor de 2 ns, ¿Qué tasas de acierto es necesaria?</li>
</ol>
</html>

   (solución)
<html>
<ol type="a">
<li>
𝑇<sub>m</sub> = 5*0.9 + (150+5)*0.1 = 4.5 + 15.5 = 20 ns
</li>
<li>
2 = 5*h + (150+5)*(1-h) => h = 153/150 => h>1.02<br>
Pero como la tasa de acierto es un valor entre 0 y 1, un valor de 1.02 supone que no es posible llegar al tiempo medio de acceso de 2ns con una memoria caché de 5ns.
</li>
</ol>
</html>


