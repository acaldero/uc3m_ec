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
Se desea desarrollar un controlador para un semáforo. El controlador dispone de una CPU de 32 bits, mapa de E/S separado y juego de instrucciones del RISC-V 32. A esta CPU se le conectan dos módulos de E/S. El primero es un cronómetro y el segundo es el módulo de E/S que controla el funcionamiento del semáforo. El módulo cronómetro dispone de los tres registros siguientes:<br>
<br>
<ul>
<li>Registro con dirección 1000. En este registro se carga el valor correspondiente a la cuenta atrás en segundos.</li>
<li>Registro con dirección 1004. En este registro se carga un 1 cuando se quiere comenzar la cuenta atrás.</li>
<li>Registro con dirección 1008. Cuando la cuenta atrás llega a 0, en este registro se carga un 1. Mientras se está realizando la cuenta atrás el valor de este registro es 0.</li>
</ul>

<ul>
El módulo de E/S que controla el semáforo dispone de tres registros:
<li>Registro con dirección 1012. En este registro se codifica el valor correspondiente al color del semáforo: 100 para el rojo, 010 para el amarillo y 001 para el verde. </li>
<li>Registro con dirección 1016. Es un registro que indica la duración en segundos correspondiente al rojo.</li>
<li>Registro con dirección 1020. Es un registro que indica la duración correspondiente al amarillo, que ocurre en la transición rojo-verde.</li>
<li>Registro con dirección 1024. Es un registro que indica la duración en segundos del verde.</li>
</ul>

Se pide:<br>
<ol type="a">
Escriba el programa ensamblador que controla el funcionamiento de este semáforo. El semáforo siempre comienza su funcionamiento en rojo.
</ol>
<ol type="a">
¿Qué ineficiencia se identifica en el programa anterior? ¿Cómo se podría resolver?
</ol>
</html>

   (solución)
<html>
<ol type="a">
ROJO:
	li 	t0, 100
	OUT 	t0, 1012
	IN 	t0, 1016
	OUT 	t0, 1000
	IN 	t0, 1
	OUT 	t0, 1004
ESPERA_ROJO:
	IN 	t0, 1008
	li 	t1, 1
	beq 	t0, t1, ESPERA_ROJO
AMARILLO:
	li 	t0, 010
	OUT 	t0, 1012
	IN 	t0, 1020
	OUT 	t0, 1000
	IN 	t0, 1
	OUT 	t0, 1004
ESPERA_AMARILLO:
	IN 	t0, 1008
	li 	t1, 1
	beq 	t0, t1, ESPERA_AMARILO
VERDE:
	li 	t0, 010
	OUT 	t0, 1012
	IN 	t0, 1024
	OUT 	t0, 1000
	IN 	t0, 1
	OUT 	t0, 1004
ESPERA_VERDE:
	IN 	t0, 1008
	li 	t1, 1
	beq 	t0, t1, ESPERA_VERDE
	beq 	x0, x0, ROJO

</ol>

<ol type="a">
La principal causa de ineficiencia es consumo de CPU en el tiempo de espera del contador. La solución sería el empleo de E/S mediante interrupciones. 
</ol>
</html>

