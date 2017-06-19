---
layout: post
title: Trabajo con Ficheros en COBOL
---
 
Vamos a crear un programa COBOL que lea un fichero, modifique los registros, y guarde
el resultado de sus operaciones en un archivo de salida.

El archivo a usar es el generado después del SORT, visto en el anterior post.

Cada registro tiene dos campos, el número y el nombre del pais. Vamos darle la vuelta
poniendo el número a la derecha del nombre.

![](http://i.imgur.com/mUBoRHt.png)

El encabezado del programa es trivial. Así que prestemos atención al ENVIRONMENT DIVISION.

**Importante recordar que hay muchas maneras diseñar este código obteniendo el mismo resultado.
Esta es una de ellas**

En el INPUT-OUPUT SECTION definimos un FILE-CONTROL con dos archivos.

IN-FILE, que usaremos como archivo de entrada y que es asignado a ENTRADA (este nombre 
de asignación deberá coincidir con la definición que usemos en el script de ejecución).

Se guarda el estado del archivo en una variable para poder identificar errores concretos 
según un código devuelto.  
[TABLA CÓDIGOS DE ERROR](http://www.escobol.com/modules.php?name=Sections&op=viewarticle&artid=21)

E idem  para el archivo de salida.


En la DATA DIVISION - FILE SECTION se definen los datos que vamos a tratar.

Los registros leidos del archivo paises los formateamos según la estructura de datos
PAISES-IN, insertando un FILLER para llenar de espacios en blanco el resto del registro, que debe 
coincidir con la longitud del archivo.

Para la salida hacemos algo similar, salvo el orden invertido de Nombre e ID, que ya nos da una idea 
de la solución de diseño que hemos elegido.
 
![](http://i.imgur.com/jNH9wCt.png)

En la WORKING STORAGE SECTION declaramos las variables para almacenar los File Status y una variable
 para controlar la lógica de nuestro algoritmo.


 
![](http://i.imgur.com/kG4E8Pl.png) 

WS-EOF tomará el valor S cuando llegemos al final de la lectura del archivo.

**100-INICIO** se ejecuta una sola vez. 
Inspecciona los File Status después de las aperturas para informar
de cualquier problema, y termina el programa si encuentra algo diferente a 00.

Por último controlamos de manera explícita si nuestro puntero de lectura está ya en el final del archivo.
Si es así, cambiará el valor de WS-EOF y no se ejecutará 200-PROCESO por la condición UNTIL.

De esta manera nos evitaremos comportamientos extraños como la inserción de un registro extra en blanco en nuestro
archivo de salida.

![](http://i.imgur.com/Aoo8RjQ.png)

Una vez hechas todas las preparaciones previas, el párrafo **200-PROCESO** queda muy simplificado:

Copia los valores de lectura a las variables asignadas a la salida.

Escribe esta salida en el archivo dado.

Y lee/se posiciona en el siguiente registro. Cuando identifique el final del archivo parará su ejecución.

![](http://i.imgur.com/Q1bnE8U.png)

Por último el párrafo **300-FIN** cierra las conexiones y termina el programa.

Este es el resultado de su ejecución:

![](http://i.imgur.com/eVNVog2.png)

:D

En este caso para las pruebas hemos creado dos JOBs , uno para compilar y enlazar, y otro para la ejecución.

El COMPILE and LINK es como el de cualquier otro visto hasta ahora.


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
//SYSLIN  DD DSNAME=SCHOOL.COBOL.OBJ(PAISES),UNIT=SYSDA,DISP=SHR   
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
//SYSIN    DD  DSN=SCHOOL.COBOL(PAISES),DISP=SHR                   
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
//SYSLIN   DD DSNAME=SCHOOL.COBOL.OBJ(PAISES),DISP=SHR             
//SYSIN    DD *                                                    
 NAME PAISES(R)                                                    
//SYSLMOD  DD DSNAME=SCHOOL.COBOL.LOAD(PAISES),DISP=SHR,RECFM=U    
//*    ARRIBA ---------------------------------------   PRINCIPAL                            
~~~

Sin embargo en el ejecutador, debemos introducir la Data Definition de ENTRADA y SALIDA tras la invocación
a nuestro programa recien compilado.

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
 DELETE SCHOOL.DATA(ARCH3)                       
 SET MAXCC=0                                     
 SET LASTCC=0                                    
//*  EJECUTAR PROGRAMA                           
//PASOEXEC EXEC PGM=PAISES                       
//ENTRADA  DD DSN=SCHOOL.DATA(ARCH2),DISP=SHR    
//SALIDA   DD DSN=SCHOOL.DATA(ARCH3),DISP=OLD,   
//            SPACE=(TRK,(1,1),RLSE),            
//            DCB=(BLKSIZE=0,LRECL=80,RECFM=FB)  
//SYSOUT   DD SYSOUT=*                           
//*                                               
~~~




Saludos :D



  










