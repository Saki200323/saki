# Bitácora de aprendizaje de la unidad 1: arquitectura del computador

## Bitacora de David Vanegas Londoño

### EJEMPLO CLASE #1
![download](https://github.com/user-attachments/assets/66316b47-6747-4d9a-9384-0e5d7f6caaeb)

``` c
/*
ejemplo.c

(c) Envite, 2004
para el wikilibro "Programación en C (fundamentos)"
bajo licencia FDL
*/

#include <stdio.h> /* Necesario para la función printf() */

int main(void) /* Función principal del programa */
{
	char resultado; 

	resultado=5+2; 
	printf("Resultado de la suma: %i\n",resultado);
	resultado=5-2; 
	printf("Resultado de la resta:%i\n",resultado);
	resultado=5*2; 
	printf("Resultado de la multiplicación: %i\n",resultado);
	resultado=5/2; 
	printf("Resultado de la división:%i\n",resultado);
	
	return(0); 

}

```

# ACTIVIDAD 1  



### ¿Qué es un computador digital moderno?
Un computador digital moderno es un sistema en el cual recibe una informacion digital que se lleva a un procesador donde lee la informacion y la almacena ahi mismo o la traslada a un lugar externo como la RAM.

### ¿Cuáles son sus partes?

Tiene unas partes fundamentales, un programa que se ejecuta, un procesador que unifica y procesa la iformacion que recibe del programa y una memoria RAM que se encarga de guardar y almacenar la informacion procesada de el procesador aunque esta informacion tambien puede quedarse almacenada en el procesador de forma interna 

# ACTIVIDAD 2  - [ ] 

### ¿Qué es entonces un programa?

Un programa es un lenguaje almacenado en memoria ROM que tiene consigo informacion lista para ser procesar y es una secuencia de informacion en lenguaje de maquina.

![softwares-de-programacion](https://github.com/user-attachments/assets/9fd322e9-dd85-4a7d-864d-026115f3060e)


### ¿Qué es un lenguaje ensamblador?

Es un sistema de simbolos que se traducen al lenguaje de maquina por medio de un ensamblador para que el programa funcione.

Ejemplo:

``` cmd

*
*      CONSTANTS
*
         CMQMDA DSECT=NO,LIST=YES
         CMQGMOA DSECT=NO,LIST=YES
         CMQA
*
*      WORKING STORAGE DSECT
*
WORKSTG  DSECT
*
COMPCODE DS F
REASON   DS F
BUFFLEN  DS F
DATALEN  DS F
OPTIONS  DS F
HCONN    DS F
HOBJ     DS F
*
BUFFER   DS CL80
BUFFER_LEN EQU *-BUFFER
*
WMD      CMQMDA DSECT=NO,LIST=NO
WGMO     CMQGMOA DSECT=NO,LIST=NO
*
CALLLST  CALL ,(0,0,0,0,0,0,0,0,0,0,0),VL,MF=L
*
⋮
END

```
### ¿Qué es lenguaje de máquina?

El lenguaje de maquina es un sistema conformado por unos y ceros que el computador es capaz de leer el computador y procesar esta información 

ejemplo:
```
10001010 00000110 10101010 11100100 10010001 11100100 10010000 00110100 01000000 01101110 10001010 00000110
10101010 11100100 10010001 11100100 10010000 00110100 01000000 01101110 10011011 00001101 11000101 11101101

10001010 00000110 10101010 11100100 10010001 11100100 10010000 00110100 01000000 01101110 10001010 00000110
10101010 11100100 10010001 11100100 10010000 00110100 01000000 01101110 10011011 00001101 11000101 11101101

10001010 00000110 10101010 11100100 10010001 11100100 10010000 00110100 01000000 01101110 10001010 00000110
10101010 11100100 10010001 11100100 10010000 00110100 01000000 01101110 10011011 00001101 11000101 11101101

```

## Direcciones de memoria

- A: Es una posicion de memoria interna que tiene la CPU
    - En lenguaje ensamblador es cuando el valor empieza con un @
    - En lenguaje de maquina es cuando el valor es 0
 
- D: Crea una copia del valor de A despues de terminar una proceso
  
- PC: Es un contador de procesos que cuenta cuantas veces se ejecuta un programa

- M=D. significa que quiero guardar un valor en la memoria

  ## EJECRCICIO

  ### Escribe un programa en lenguaje ensamblador que guarde en la posicion 32 de la RAM un 100

  ``` 
  @100
  D = A
  @32
  M = D
  ```

# RETO
### 1) Carga en D el valor 1978.

```
@1978
D=A
```

### 2) Guarda en la posición 100 de la RAM el número 69.

```
@69
D=A
@100
M=D
```

### 3) Guarda en la posición 200 de la RAM el contenido de la posición 24 de la RAM.

```
@24
D=M
@200
M=D
```

### 4) Lee lo que hay en la posición 100 de la RAM, resta 15 y guarda el resultado en la posición 100 de la RAM.

```
@15
D=A
@100
M=M-D
```

### 4.1) Lee lo que hay en la posición 100 de la RAM, resta 15 y guarda el resultado en la posición 200 de la RAM.

```
@15
D=A
@100
D=M-D
@200
M=D
```

### 5) Suma el contenido de la posición 0 de la RAM, el contenido de la posición 1 de la RAM y con la constante 69. Guarda el resultado en la posición 2 de la RAM.

```
@69
D=A
@1
D=D+M
@0
D=D+M
@2
M=D
```

### 6) Si el valor almacenado en D es igual a 0 salta a la posición 100 de la ROM.
```
@100
D;JEQ
```

### 7) Si el valor almacenado en la posición 100 de la RAM es menor a 100 salta a la posición 20 de la ROM.
```
@100
D=M
@100
D=D-A
@20
D;JLT

```
### 8) Considera el siguiente programa:
```
@var1
D=M
@var2
D=D+M
@var3
M=D
```
+ ¿Qué hace este programa?

   Este programa lo que hace es registrar la **@var1** y la **@var2** y sumarlas y el resultado de la suma se guarda en la **@var3**. 

+ En qué posición de la memoria está var1, var2 y var3? ¿Por qué en esas posiciones?

   - Var1: en la RAM @16
   - Var2: en la RAM @17
   - Var3: en la RAM @18
 
como las psiciones del 1 al 15 estan reservadas las variables se comienzan a guardar apartir de esta del 16 en adelante

### 9) Considera el siguiente programa:
```
// i = 1
@i
M=1
// sum = 0
@sum
M=0
...
// sum = sum + i
@i
D=M
@sum
M=D+M
// i = i + 1
@i
D=M+1
@i
M=D
```

+ ¿Qué hace este programa?
  	- guarda en la variable **i** el numero 1, pasa a la variable **sum** y lo hace 0 or lo que queda i=1 y sum=0 despues en la variable sum se guarda el valor de la suma entre las dos variables y se le suma 1 a la 	  variable **i** 
+ ¿En qué parte de la memoria RAM está la variable i y sum? ¿Por qué en esas posiciones?
  	- la variable **i** esta guardada en la posicion @16 y la variable **sum** en la psicion @17 porque como en el ejemplo anterior apartir de la 16 las variables estan disponibles.
+ Optimiza esta parte del código para que use solo dos instrucciones:
```
// i = i + 1
@i
D=M+1
@i
M=D
```

forma optimizada:
```
@i
M=D+1
```

### 10) Las posiciones de memoria RAM de 0 a 15 tienen los nombres simbólico R0 a R15. Escribe un programa en lenguaje ensamblador que guarde en R1 la operación 2 * R0.
```
@R0
D=M
D=D+M
@R1
M=D
```

### 11) Considera el siguiente programa:
```
// i = 1000
@1000
D=A
@i
M=D
(LOOP)
// if (i == 0) goto CONT
@i
D=M
@CONT
D;JEQ
// i = i - 1
@i
M=M-1
// goto LOOP
@LOOP
0;JMP
(CONT)
```

- ### ¿Qué hace este programa?

Crea un loop de 1000 repeticiones.

- ### En qué memoria está almacenada la variable i? ¿En qué dirección de esa memoria?

  La variable *i* está almacenadaen la **RAM** y está en la direccion @16

- ### ¿En qué memoria y en qué dirección de memoria está almacenado el comentario //i = 1000?

En la memoria **ROM** y en la dirección @1000 para hacer el loop de 1000 repeticiones

- ### ¿Cuál es la primera instrucción del programa anterior? ¿En qué memoria y en qué dirección de memoria está almacenada esa instrucción?

la prmera instruccion está en la memoria **RAM** y en la direccion 0 en la memoria **ROM**

- ### ¿Qué son CONT y LOOP?

	- CONT: es un contador
   	- LOOP: es una cantidad de repeticiones que hace de un pedacido del programa

- ### ¿Cuál es la diferencia entre los símbolos i y CONT?

La diferencia principal entre las dos es que *i* no es una variable definida por eso empieza en @16 en cambio *CONT* si está definida por eso se coloca en @12


## 12) Implemente en ensamblador:

```
R4 = R1 + R2 + 69
```

sería asi:

```
@69
D=A
@R2
D=D+M
@R1
D=D+M
@R4
M=D
```

## 13) Implemente en ensamblador:

```
if R0 >= 0 then R1 = 1
else R1 = –1

(LOOP)
goto LOOP
```

sería asi:

```
@R0
D=M
@POSITIVE
D;JGE        
@NEGATIVE
0;JMP        

(POSITIVE)
@1
D=A           
@R1
M=D           
@LOOP
0;JMP         

(NEGATIVE)
@1
D=-A          
@R1
M=D           
@LOOP
0;JMP         

(LOOP)
@LOOP
0;JMP         
```

## 14) Implemente en ensamblador:

```
R4 = RAM[R1]
```

sería asi:

```
@R1
A=M 
D=M 
```


## 15) Implementa en ensamblador el siguiente problema. En la posición R0 está almacenada la dirección inicial inicial de una región de memoria. En la posición R1 está almacenado el tamaño de la región de memoria. Almacena un -1 en esa región de memoria:

### sería asi:

```
@R1         
D=M         
@SIZE       
M=D          

@LOOP        
@SIZE        
D=M         
@END        
D;JEQ       

@START       
A=M         
M=-1        

@START       
M=M+1       
@SIZE        
M=M-1        
@LOOP        
0;JMP        

(END)       
@END         
0;JMP        
```

## 16) Implemente en ensamblador:

```
int[] arr = new int[10];
int sum = 0;
for (int j = 0; j < 10; j++) {
    sum = sum + arr[j];
}
```

sería asi:

```
@256   
D=A
@addrArr
M=D   

@0
D=A
@sum
M=D     

@0
D=A
@j
M=D   


(LOOP)
@j
D=M    
@10
D=D-A   
@END
D;JGE   


@addrArr
D=M   
@j
A=D+M   
D=M    
@sum
M=M+D  


@j
M=M+1


@LOOP
0;JMP


(END)
@END
0;JMP   

```

###  1) ¿Qué hace este programa?

* Este programa crea un arreglo de enteros de tamaño 10 y luego suma todos sus elementos. Al final, la variable sum contiene la suma de los elementos del arreglo.

###  2) ¿Cuál es la dirección base de arr en la memoria RAM?

* En el código ensamblador dado, arr se almacena en la posición de memoria 256. Esta dirección es elegida arbitrariamente para ilustrar el ejemplo, ya que en un sistema real, la dirección podría ser determinada por el sistema operativo o el entorno de ejecución.

###  3) ¿Cuál es la dirección base de sum en la memoria RAM y por qué?

* sum se almacena en una posición de memoria específica. Para propósitos de este ejemplo, asumo que se encuentra en una dirección arbitraria, por ejemplo, 257 (justo después de arr). En un sistema real, el compilador o el ensamblador asignaría una dirección específica para esta variable. 

###  4) ¿Cuál es la dirección base de j en la memoria RAM y por qué?

* j se almacena en otra posición de memoria específica, por ejemplo, 258 (justo después de sum). De nuevo, esto es una decisión de implementación y podría variar según el sistema y la disposición de las variables en la memoria.

## 17) Implemente en ensamblador:

```
if ( (D - 7) == 0) goto a la instrucción en ROM[69]
```

sería asi:

```
@D    
D=M    
@7     
D=D-A    
@69     
D;JEQ   

```

## 18) Utiliza [esta](https://nand2tetris.github.io/web-ide/bitmap) herramienta para dibujar un bitmap en la pantalla.

## 19) Analiza el siguiente programa en lenguaje de máquina:

```
0100000000000000
1110110000010000
0000000000010000
1110001100001000
0110000000000000
1111110000010000
0000000000010011
1110001100000101
0000000000010000
1111110000010000
0100000000000000
1110010011010000
0000000000000100
1110001100000110
0000000000010000
1111110010101000
1110101010001000
0000000000000100
1110101010000111
0000000000010000
1111110000010000
0110000000000000
1110010011010000
0000000000000100
1110001100000011
0000000000010000
1111110000100000
1110111010001000
0000000000010000
1111110111001000
0000000000000100
1110101010000111
```
## ANALISIS

```
// Línea 1
@0       //  carga 0 en el registro A
D=A      //  D = A

// Línea 2
@16      //  carga 16 en el registro A
D=D&A    //  realiza la operación D = D & A

// Línea 3
@19      //  carga 19 en el registro A
D=D&A    //  realiza la operación D = D & A

// Línea 4
@16      //  carga 16 en el registro A
D=D-A    //  realiza la operación D = D - A

// Línea 5
@0       //  carga 0 en el registro A
D=D&A    //  realiza la operación D = D & A

// Línea 6
@4       //  carga 4 en el registro A
D=D&A    //  realiza la operación D = D & A

// Línea 7
@16      //  carga 16 en el registro A
D=D-A    //  realiza la operación D = D - A

// Línea 8
@4       //  carga 4 en el registro A
D=D&A    //  realiza la operación D = D & A

// Línea 9
@16      //  carga 16 en el registro A
D=D-A    //  realiza la operación D = D - A

// Línea 10
@0       //  carga 0 en el registro A
D=D&A    //  realiza la operación D = D & A

// Línea 11
@16      //  carga 16 en el registro A
D=D-A    //  realiza la operación D = D - A

// Línea 12
@4       //  carga 4 en el registro A
D=D&A    //  realiza la operación D = D & A

// Línea 13
@16      //  carga 16 en el registro A
D=D-A    //  realiza la operación D = D - A

// Línea 14
@0       //  carga 0 en el registro A
D=D&A    //  realiza la operación D = D & A

// Línea 15
@16      //  carga 16 en el registro A
D=D-A    //  realiza la operación D = D - A

// Línea 16
@4       //  carga 4 en el registro A
D=D&A    //  realiza la operación D = D & A
```

El código realiza una serie de operaciones lógicas y aritméticas que, en muchos casos, resultan en el valor 0 para D después de cada cálculo. La lógica se basa en operaciones AND y restas entre el registro D y el valor en el registro A. El valor de D alterna entre 0 y -16 a lo largo del código debido a las operaciones realizadas.

En términos generales, el código parece estar diseñado para poner el valor final en D como 0, a pesar de que se realizan cálculos intermedios que resultan en -16 en algunos pasos.

## 20) Implementa un programa en lenguaje ensamblador que dibuje el bitmap que diseñaste en la pantalla solo si se presiona la tecla “d”.

```

@0x1000  
D=M    

// Esperar a que se presione la tecla 'd'
@KBD     
D=M   

@0x64    
D=D-A    


@END    
D;JNE   

// Dibuja el bitmap en la pantalla
@0x6000  
D=A      
@0x1000  
D=M      

@SCREEN  
M=D     


(END)
@END
0;JMP  

```
