## Materiales para Estructura de Computadores

<html>
<h2><ul>
<li>License <a href="http:/creativecommons.org/licenses/by-nc/4.0/">CC BY-NC 4.0</a> </li>
<li>Curso 2022-2023</li>
</ul></h2>
</html>


### Ejercicio 1

   (enunciado) Implemente una función/subrutina strlen que se le pase como argumento la dirección de una cadena de caracteres y devuelva el número de caracteres en la cadena. 
               Siga el convenio de paso de parámetros y uso de registros visto en clase.
    
   (solución) El siguiente código RISC-V implementa la funcionalidad pedida.

```
.text
  # strlen(a0 -> "hola") -> 4
  strlen: # acc = 0
          # i = 0
          # while a0[i] != 0:
          #    acc+=1; i+=1;
          # return acc
          li t1 0
   loop1: lbu t0 0(a0)
          beq t0 x0 end1
          addi t1 t1 1
          addi a0 a0 1
          j loop1
    end1: mv a0 t1
          jr ra 
```

### Ejercicio 2

   (enunciado) Implemente un programa principal (main:) que use la rutina/función strlen del ejercicio 1 para calcular e imprimir la longitud de las cadenas "hola" y "mundo". 
               Siga el convenio de paso de parámetros y uso de registros visto en clase.
    
   (solución) El siguiente código RISC-V implementa la funcionalidad pedida.

```
.data
  str1: .string  "hola"
  str2: .string  "mundo"
  
.text
  strlen: li t1 0
   loop1: lbu t0 0(a0)
          beq t0 x0 end1
          addi t1 t1 1
          addi a0 a0 1
          j loop1
    end1: mv a0 t1
          jr ra 
   
  main:
    # push ra
    addi sp sp -4
    sw ra 0(sp)
    
    # strlen("hola")
    la  a0 str1
    jal ra strlen   
    
    # print(a0)
    li a7 1
    ecall
 
    # strlen("mundo")
    la  a0 str2
    jal ra strlen  

    # print(a0)
    li a7 1
    ecall

    # pop ra
    lw ra 0(sp)
    addi sp sp 4
    
    # return
    jr ra
```

