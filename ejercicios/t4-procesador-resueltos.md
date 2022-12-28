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
Rellene la siguiente tabla con las operaciones elementales y señales de control asociadas a la instrucción "BEQ Rf1, Rf2, desp".

<table>
<tr>
<td>Ciclo</td>
<td>Op. Elemental</td>
<td>Señales activadas (resto a 0)</td>
</tr>
<tr>
<td>...</td>
<td>...</td>
<td>...</td>
</tr>
</table>
</html>


   (solución)
<html>
<table>
<tr>
<td>Ciclo</td>
<td>Op. Elemental</td>
<td>Señales activadas (resto a 0)</td>
</tr>

<tr>
<td>0</td>
<td>Rf1 - Rf2</td>
<td>SelA=10101, SelB=10000, SelCop=1011, MC, C7, M7, SelP=11, C=0000, B=0, A0=0</td>
</tr>

<tr>
<td>1</td>
<td>If (Z == 0)<br>
    &nbsp;&nbsp;&nbsp;&nbsp; goto fetch<br>
    else next</td>
<td>MADDR=0, C=0110, B=1, A0=0</td>
</tr>

<tr>
<td>2</td>
<td>RT1 ← PC</td>
<td>T2, C4, C=0000, B=0, A0=0</td>
</tr>

<tr>
<td>3</td>
<td>RT2 ← IR (dir)</td>
<td>Size = 10000, Offset=00000, T3, C5, C=0000, B=0, A0=0</td>
</tr>

<tr>
<td>4</td>
<td>PC ← RT1 +RT2</td>
<td>MA, MB=01, SelCop=1010, MC, T6, C2, C=0000, B=1, A0=1</td>
</tr>
</table>
</html>

