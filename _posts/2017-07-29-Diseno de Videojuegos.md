---
layout: post
title: Diseno de Videojuegos
---
 

 
 
 
![](http://i.imgur.com/t3AZC3h.png)

Por último el párrafo **300-FIN**


El JCL de COMPILACIÓN y ENLACE usado es este. _En este punto no nos importa
entradas ni salidas. Solo la compilación. Hay muchos errores que pueden venir después, 
en la ejecución, y que necesitarán que se compile de nuevo en este paso
después de modificar el código en COBOL para
resolverlos._
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


El JCL de EJECUCIÓN. _Véase que las entradas son los archivos secuenciales 
ordenados usando un sort simple. Para la salida he elegido que sea un miembro de
un dataset._
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



  










