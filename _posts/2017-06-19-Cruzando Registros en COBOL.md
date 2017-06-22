---
layout: post
title: Cruzando Registros en COBOL
---
 
En esta ocasión vamos a trabajar con dos ficheros que tienen un índice similar. Los ordenaremos y 
crearemos un fichero que será el resultado de unir sus registros de manera ordenada.

![](http://i.imgur.com/M3ywtWz.png)

![](http://i.imgur.com/XeLr8Ur.png)


![](http://i.imgur.com/CoP3EkB.png)


![](http://i.imgur.com/ZmJkuPH.png)


![](http://i.imgur.com/bu6CYJJ.png)

Los ordenamos en un proceso muy similar al mostrado en un 
[ANTERIOR POST](https://radw2020.github.io/2017/06/17/JCL-SORT-en-HOST/).
Podemos crear un job ocn un paso, y ejecutarlo dos veces cambiando el SORTIN y el SORTOUT. O podemos
crear un job con dos pasos y ordenar los dos archivos de una tacada.
En este caso van a ser archivos secuenciales, aunque también podrían ser miembros de un fichero secuenciales
como en el ejemplo del enlace anterior.

Después de ordenar únicamente por su índice de dos números de manera ascendente, tenemos:



![](http://i.imgur.com/SHBo9aT.png)


![](http://i.imgur.com/TVHHYcT.png)

La estructura de las direcciones school queda tal que así:

![](http://i.imgur.com/Yqr4Zf4.png)

Una vez tenemos nuestros archivos ordenados, podemos empezar a codificar el programa COBOL.
El programa va a leer de dos archivos, que tienen una estructura similar. Registro a registro 
los va a comparar y a ir escribiendo en el archivo de salida de manera ordenada. 

# ENVIRONMENT DIVISION

![](http://i.imgur.com/5iZEaDr.png)

En el input output section se va a asignar las dos entradas, estos nombres ENTRADA1,
ENTRADA2, y SALIDA deberán coincidir con los nombres que pongamos en el JCL de ejecución
de nuestro programa compilado.
Por lo pronto a nivel de COBOL ya podemos trabjar sobre IN-FILE1, IN-FILE2 y OUT-FILE.

# DATA DIVISION

Aquí podemos definir los los FD de nuestros archivos.
En este paso asignamos el formato de registro que tendrá cada linea que leamos. En este
caso CIUDADES y PAISES.

![](http://i.imgur.com/h8osAZ3.png)

Los registros del archivo de salida también deberán ser definidos en este punto.
En este ejemplo los tres archivos tienen una estructura similar para no despistar. 
El nombre elegido para la variable conetnedora es CROSS-OUT.

![](http://i.imgur.com/UZPImlr.png)

En los tres casos usaremos las variables de nivel 05 para mover datos en el proceso
COBOL y las variables de nivel 01 para escribir la salida.

En la WORKING STORAGE SECTION se definen las tres variables que contendrán 
los file status de las conexiones con los archivos. Y una variable WS-EOF para 
controlar el fin de fila.

En este ejemplo hay que prestar atención por que su diseño es determinante para 
el algoritmo que vamos a implementar. 

![](http://i.imgur.com/pFZqcgl.png)

Es un alfanumérico de dos caracteres que usaremos
como booleano para determinar los cuatro estados posibles:
 - los dos archivos están sin terminar de leer 'NN'
 - El primer archivo ha terminado de leer 'SN'
 - El segundo archivo ha terminado de leer 'NS'
 - Los dos archivos han terminado 'SS' 	 

# PROCEDURE DIVISION

En el procedure division tenemos tres PERFORM principales

  - 100-INICIO para abrir conexiones y controlas errores en los File Status. 
 Si se encuentra un error de cualquier tipo en este paso, se aborta.
  - 200-PROCESO que se va a ejecutar en bucle hasta que la variable de control
  de End Of File de nivel 01 tenga como valor 'SS'. 
  - 300-FIN que cierra las conexiones y termina el programa.

![](http://i.imgur.com/MJxHZsZ.png)

Párrafo inicio

![](http://i.imgur.com/VUK3k8D.png)

Nótese que las lecturas a los ficheros están implementadas en párrafos. 
Al final de este párrafo se hace una lectura anticipada para evitar 
la entrada de un registro en blanco según tenemos implementado el flujo
general del proceso.

![](http://i.imgur.com/L7oKMbI.png)

También tienen párrafos independientes la escritura de datos en la salida. 
Uno para escribir la lectura del archivo1 y otro para el archivo2.

![](http://i.imgur.com/jWPpUE7.png)

Hace uso de WS-EOF para evaluar y elegir una opción. 

Para el caso 'NN' es sencillo,
compara, y el que sea menor es el que se escribe en la salida y se lee de nuevo de su
conexión.

Cuando es 'SS' fácil, termina el bucle porque ya se ha determinado así con el UNTIL.

Con WS-EOF en 'NS' ha llegado al fin del segundo archivo. Entonces lee escribe del
primero y los escribe. No llega a comparar.

En WS-EOF con 'SN' es lo mismo pero para el otro archivo.

Este algoritmo se podría haber reducido bastante, pero me ha parecido esta manera
explícita más didáctica y simple para mí. 

![](http://i.imgur.com/t3AZC3h.png)

Por último el párrafo 300-FIN.


El JCL de COMOILACIÓN y ENLACE usado es este. En este punto no nos importa
entradas ni salidas. Solo la compilación. Hay muchos errores que pueden venir después, 
en la ejecución, y que necesitarán que se compile de nuevo en este paso
después de modificar el código en COBOL para
resolverlos.
~~~
//IBMUSERC JOB NOTIFY=&SYSUID,MSGCLASS=X,MSGLEVEL=(1,1)           
//*JOBLIB   DD DSN=SCHOOL.COBOL.LOAD,DISP=SHR                     
//*--------------------------------------------------------------*
//*   AQUI DEBAJO COMPILA Y CREA EL EJECUTABLE                    
//*--------------------------------------------------------------*
//PASOCOMP EXEC PGM=IGYCRCTL,REGION=2048K,PARM='LIB,'             
//SYSPRINT DD   SYSOUT=*                                          
//*--------------------------------------------------------------*
//*   AQUI DEBAJO SE INDICA DONDE ESTAN LAS COPYS                 
//*--------------------------------------------------------------*
//SYSLIB   DD  DSN=SCHOOL.COBOL.COPYS,DISP=SHR                    
//* DEBAJO --------------------------------------------- RUTINAS  
//SYSLIN  DD DSNAME=SCHOOL.COBOL.OBJ(SORTCROS),                   
//           UNIT=SYSDA,DISP=SHR                                  
//*            DISP=(MOD,PASS),SPACE=(TRK,(3,3)),                 
//*            DCB=(BLKSIZE=3200)                                 
//*        DD  DSNAME=SCHOOL.COBOL.OBJ(SUBRUTINA)                 
//* ARRIBA --------------------------------------------- RUTINAS  
//SYSUT1   DD  UNIT=SYSDA,SPACE=(CYL,(1,1))                       
//SYSUT2   DD  UNIT=SYSDA,SPACE=(CYL,(1,1))                       
//SYSUT3   DD  UNIT=SYSDA,SPACE=(CYL,(1,1))                       
//SYSUT4   DD  UNIT=SYSDA,SPACE=(CYL,(1,1))                       
//SYSUT5   DD  UNIT=SYSDA,SPACE=(CYL,(1,1))                       
//SYSUT6   DD  UNIT=SYSDA,SPACE=(CYL,(1,1))                       
//SYSUT7   DD  UNIT=SYSDA,SPACE=(CYL,(1,1)) 
//*    DEBAJO ---------------------------------------    COBOL PPAL 
//SYSIN    DD  DSN=SCHOOL.COBOL(SORTCROS),DISP=SHR                  
//*    ARRIBA ---------------------------------------    COBOL PPAL 
//PASOLKED EXEC PGM=HEWL,COND=(5,LT,PASOCOMP),PARM=''               
//SYSLIB   DD  DSN=CEE.SCEELKED,DISP=SHR                            
//         DD  DISP=SHR,DSN=DSN810.SDSNLOAD                         
//         DD  DISP=SHR,DSN=IMS1010.SDFSRESL                        
//*        DD  DISP=SHR,DSN=CICSTS21.CICS.SDFHLOAD                  
//         DD  DISP=SHR,DSN=ISP.SISPLOAD                            
//         DD  DISP=SHR,DSN=GDDM.SADMMOD                            
//SYSUT1   DD  DSN=&SYSUT1,UNIT=SYSDA,SPACE=(1024,(200,20)),        
//             DCB=BLKSIZE=1024                                     
//SYSPRINT DD  SYSOUT=*                                             
//*    DEBAJO ---------------------------------------   PRINCIPAL   
//SYSLIN   DD DSNAME=SCHOOL.COBOL.OBJ(SORTCROS),DISP=SHR            
//SYSIN    DD *                                                     
 NAME SORTCROS(R)                                                   
//SYSLMOD  DD DSNAME=SCHOOL.COBOL.LOAD(SORTCROS),DISP=SHR,RECFM=U   
//*    ARRIBA ---------------------------------------   PRINCIPAL                                         
~~~


El JCL de EJECUCIÓN. Véase que las entradas son los archivos secuenciales 
ordenados usando un sort simple. Y para la salida he elegido un miembro de
un dataset CRUCE.
~~~
//IBMUSERG JOB MSGCLASS=X,MSGLEVEL=(1,1),            
// NOTIFY=&SYSUID                                    
//*                                                  
//JOBLIB   DD  DSN=SCHOOL.COBOL.LOAD,DISP=SHR        
//* BORRADO DE FICHERO                               
//BORRADO EXEC PGM=IDCAMS                            
//SYSPRINT DD SYSOUT=*                               
//SYSOUT   DD SYSOUT=*                               
//SYSIN    DD *                                      
 DELETE SCHOOL.DATA(CRUCE)                           
 SET MAXCC=0                                         
 SET LASTCC=0                                        
//*  EJECUTAR PROGRAMA                               
//PASOEXEC EXEC PGM=SORTCROS                         
//ENTRADA1 DD DSN=SCHOOL.FICHERO1.ORDENADO,DISP=SHR  
//ENTRADA2 DD DSN=SCHOOL.FICHERO2.ORDENADO,DISP=SHR  
//SALIDA   DD DSN=SCHOOL.DATA(CRUCE),DISP=OLD,       
//            SPACE=(TRK,(1,1),RLSE),                
//            DCB=(LRECL=80,RECFM=FB)                
//SYSOUT   DD SYSOUT=*                               
//*                                                  
~~~


El resultado final debería ser algo como esto:

![](http://i.imgur.com/5QIgZwe.png)


Saludos coboleros:D



  










