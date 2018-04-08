---
layout: post
title: Hyperledger Fabric
---

En este artículo voy a  pasar directamente a comentar sonre Hyperledger Fabric pero si eres un no iniciado y quieres primero romper el hielo con esta tecnología, puedes visitar [www.ibm.com/blockchain/hyperledger.html](https://www.ibm.com/blockchain/hyperledger.html) o en la wikipedia [wiki/Hyperledger](https://es.wikipedia.org/wiki/Hyperledger).


![](https://hyperledger-fabric.readthedocs.io/en/release-1.1/_images/hyperledger_fabric_logo_color.png)

Hyperledger Fabric es especial porque permite a las entidades transmitir informacion confidencial sin pasar por una autoridad central. Esto se consigue mediante los canales que se pueden configurar para funcionar dentro de la red, y por la división de tareas con las que se caracterizan a los diferentes nodos dentro de la red.

Provee una arquitectura modular, que permite diferentes componentes con funcionalidades como el "consenso" o los"servicios para afiliados" ser tipo plug-and-play.

Por último, es conveniente recordar que, al contrario que Bitcoin que es un chain público, Hyperledger Fabric permite un despliegue **permisionado**.

En palabras de su director:
*Si tienes una gran red de blockchain y desea compartir datos solo con ciertas partes, puede crear un canal privado con solo esos participantes. Es lo más distintivo de Fabric en este momento.*

Brian Behlendorf, Director Ejecutivo de Hyperledger, The Linux Foundation

## Distribución de Roles
#### Clients
Son aplicaciones que actuan en nombre de una persona que propone una transaccion.
#### Peers
Mantienen el estado de la red y una copia del ledger. Pueden ser de dos tipos:
* **Endorsers** (que simula y aplica la transaccion)
* **Commiters** (que verifica y valida la transacción después de un endorsing y antes subir la transacción al blockchain)

#### Ordering Service
Paso intermedio entre el Endorser y el Commiter que ordena las transacciones en un bloque y lo entrega al Committer Peer.

![](https://www.researchgate.net/profile/Xueping_Liang/publication/320337312/figure/fig2/AS:550838383120385@1508341512997/Data-Sharing-and-Collaboration-Using-Hyperledger-Fabric-and-Channel-for-Mobile-Users.png)

# Alncanzar el Consenso
#### Transaction endorsement
Es la respuesta firmada al resultado de simular una transacción. Es una regla configurable según el diseño que queramos hacer y puede ser diferente para cada chaincode (similar a un smartcontract) y por ende, para cada canal.

Esto se conoce como 'Endorsement Policy'.

Cada Endorser simula la transacción propuesta, sin actualizar el Ledger, y la devuelve validada a Client para que este la use en su flujo de trabajo.


#### Ordering
Las transacciones que ocurren en un intervalo dado son ordenadas y aplicadas en orden secuencial.

En Fabric 1.0 el 'ordering' es elegible, por defecto usa el módulo llamado Kafka, pero podríamos implementar otros a conveniencia.


#### Validation and commitment

El 'commiter peer' valida la transacción. Basicamente, compara que la simulación de endorser y el 'world state' coincidan y entonces la transaccion es escrita en el 'ledger' y el 'world state' actualizado.


# Canales
Los canales permiten que diferentes organizaciones que usan una misma red puedan gestionar multiples blockchains en ella.

Solo los miembros del canal en el que la transaccion se ha llevado a cabo pueden ver los detalles de esa transacción.

En otras palabras, los canales parten la red según la visibilidad que tienen los 'stakeholders' sobre las transacciones.

Solo los miembros del canal están involucrados en el consenso, mientras otros miembros de la red no ven las transacciones del canal.

![](https://prod-edxapp.edx-cdn.org/assets/courseware/v1/b23a6aaaa627620a0ab161c556ff87b3/asset-v1:LinuxFoundationX+LFS171x+3T2017+type@asset+block/Key_Components_Channels.png)


## Base de datos de Estado
Fabric permite el uso de LevelDB o de CouchDB para el 'state database'.
![](https://prod-edxapp.edx-cdn.org/assets/courseware/v1/9fa87a2726077cff05169f85584224ac/asset-v1:LinuxFoundationX+LFS171x+3T2017+type@asset+block/State_Database.png)

## Smart Contracts
Los 'smart contracts' son programas que contienen la lógica necesaria para ejecutar transacciones y modificar el estado de los 'assets' en el 'ledger'.

En Hyperledger Fabric esto se le conoce como 'chaincode' y están escritas en Go. El chaincode funciona como la lógica de negocio para la red Hyperledger Fabric. De esta manera se dirije la gestión de los 'assets' dentro de la red.


## Membership Service Provider (MSP):

Es un componente que define las reglas de validación de indentidad, autenticación y acceso a la red.

El MSP gestiona los IDs de usuario y autentica a los 'clients' que solicitan acceso. Esto incluye proveer de credenciales para que puedan proponer transacciones.

El MSP hace uso del 'Certificate Autority', que es una interfaz tipo plu-and-play que verifica o revoca certificados de usuario después de confirmar la identidad.

MSP viene por defecto con la interfaz Fabric-CA API funcionando, pero como es un componenete modular puede ser por  otra autoridad certificadora externa que desee usarse.

De hecho, un solo hyperledger puede ser controlado por diferentes MSP de diferentes organizaciones.

![](https://prod-edxapp.edx-cdn.org/assets/courseware/v1/2fe3f7dc2fa52699a96ef7948432113b/asset-v1:LinuxFoundationX+LFS171x+3T2017+type@asset+block/The_role_of_membership_service_provider.jpg)
 







