## Materiales para Estructura de Computadores

<html>
<h2><ul>
<li>License <a href="http:/creativecommons.org/licenses/by-nc/4.0/">CC BY-NC 4.0</a> </li>
<li>Curso 2022-2023</li>
</ul></h2>
</html>


### Ejercicio 1

   (enunciado)
Se desea desarrollar un controlador para un semáforo. El controlador dispone de una CPU de 32 bits, mapa de E/S separado y juego de instrucciones del RISC-V 32. A esta CPU se le conectan dos módulos de E/S. El primero es un cronómetro y el segundo es el módulo de E/S que controla el funcionamiento del semáforo.

El módulo cronómetro dispone de los tres registros siguientes:
  * Registro con dirección 1000. En este registro se carga el valor correspondiente a la cuenta atrás en segundos.
  * Registro con dirección 1004. En este registro se carga un 1 cuando se quiere comenzar la cuenta atrás.
  * Registro con dirección 1008. Cuando la cuenta atrás llega a 0, en este registro se carga un 1. Mientras se está realizando la cuenta atrás el valor de este registro es 0.

El módulo de E/S que controla el semáforo dispone de cuatro registros:
  * Registro con dirección 1012. En este registro se codifica el valor correspondiente al color del semáforo: 100 para el rojo, 010 para el amarillo y 001 para el verde. 
  * Registro con dirección 1016. Es un registro que indica la duración en segundos correspondiente al rojo.
  * Registro con dirección 1020. Es un registro que indica la duración correspondiente al amarillo, que ocurre en la transición rojo-verde.
  * Registro con dirección 1024. Es un registro que indica la duración en segundos del verde.

<html>
Se pide:<br>
<ol type="a">
<li>Escriba el programa ensamblador que controla el funcionamiento de este semáforo. El semáforo siempre comienza su funcionamiento en rojo.</li>
<li>¿Qué ineficiencia se identifica en el programa anterior? ¿Cómo se podría resolver?</li>
</ol>
</html>

