#COMPUTACION_EN_LA_NUBE (Pasa de verse HW a SW)
Alquilar los recursos a un proveedor de servicios en la nube
- SERVICIOS--> Potencia computo, Almacenamiento, Red, Analisis 
- BENEFICIOS-->Fiabilidad(bck) ,Velocidad,Escalabilidad,(↑->)Rentabilidad,Simplicidad
#### TIPOS DE NUBE:
#Publica (Alquilan el HW + flexible) ,
#Privada Crea un entorno de nube en su propio centro de datos y dan servicio de simulacion publica a los usuarios) 
#Hibrida Mezcla de publica y privada Ejecutan las aplicaciones en el lugar mas adecuado.
### TIPOS DE SERVICIO 
#Infraestructura-->  No tiene HW Local ejecutan las app en el proveedor
#Plataforma  --> El proveedor te da el entorno apropiado para crear , probar e implementar las aplicaciones .(Sin instalar SO , servidores Web ni actualizaciones)
#Software  -->SW que se aloja y administra de manera centralizada
# AWS : _Plataforma de la compañia Amazon que da servicios en la nube ofreciendo velocidad ,seguridad y optimizando los costes_
### SERVICIOS 
#EC2 --> Maquinas virtuales 
#EC2_AUTOESCALING --> Implementa y decrementa las intancias segun convenga 
@PRECIOS -->BAJO DEMANDA(↑servidor)/ON POT (h NO HABITUALES)/RESERVADAS
@CONFIG EC2 -->TPEDOCARGD , Tipo instancia , Par claves , Etiquetas ,Documentacion usuario,Opcion Almacenamiento,Configuracion Red,Grupo de seguridad , Recurso de IAM,AMI
@DISCO DURO -->EBS (Para cargas de trabajo de altas transaciones Ejemplo :BBDD)
#LAMBDA  --> Ejecuta codigo sin necesidad de servidores 
#ELASTIC_BENSTAC --> Implementa ,escala servicios y aplicaciones en la web de servidores 
#AMAZON_ROUTE_53 --> Sistema de nombre de dominio escalable que traduce las ip a nombres de dominio y dirige a los usuarios a sus aplicaciones
#GATEWAY -->Permite conectar las redes privadas a una 1 unica puerta de enlace
#VPN --> Tunel privado y seguro para ir desde tu RED hacia AWS
#ELB BALANCING--> Balanceador de carga que distribuye el trafico de red de AWS
#AMAZON CLOUD FRONT --> Entrega archivos
#DIRECT CONNECT --> Conexion de red privado que reduce costes y amplia el ancho de banda
## VPC 
- PERMITE --> Tener tu propia red privada en AWS con redes publicas y privadas (NAT para accceso a internet) 
--PERTENECER A 1 REGION ,
-- Tienen minimo 1 ip publica y otra privada con su GATEWAY
-- Especificar un intervalo de ip y hacer subredes 
-- Crear enrutamiento (Determina la direccion del trafico )
-- Hacer Grupos de Seguridad
### ALMACENAMIENTOS EN LA NUBE 
#S3 -->Almacenamiento de objetos que ofrece escalabilidad, disponibilidad de datos, seguridad y rendimiento su unidad principal se llama BUCKET

#Bucket  -->Contenedor logico Almacenar objetos (maximo 5 teras por objeto)
-Hasta 100 Bukets 
-Nombres unicos y asociados a una region
-Cada bucket contiene sus datos y metadatos
-Se pueden controlar accesos
-Lectura y escritura rapida
_*BENEFICIOS*__: Escalabilidad , durabilidad ,seguridad y disponibilidad

#StorageServiceGlacier--> Para guardar datos que no vas acceder con frecuencia (MAS ECONOMICO PERO MAS LENTO)
#EBS Elastic Block Store (ELASTIC FILE SISTEM) -> Almacenamiento por bloques EC2 (Altas transaciiones USO INTENSO)
#EFS : Sistema de archivos de Network File System (NFS) elástico escalable (Se agranda o se encoje segun el almacenamiento del momento)
### CONTROL DE VERSIONES -->
- SW que registra los cambios en 1 o varios archivos a lo largo del tiempo
### TIPOS DE SISTEMAS DE CONTROL DE VERSIONES  
#LOCALES (Todo esta en tu PC) + (no es necesario internet) - (Si rompe pierdes todo)
#CENTRALIZADOS 1 SERVIDOR CENTRAL (con todas las versiones) Y los clientes solo COGEN LA VERSION 1 VERSION ) +(si se rompe el pc tienes el servidor central ) - Desventaja si se rompe el servidor no tienes mas versiones 
#SDISTRIBUIDOS (El cliente se puede descargar todas las versiones y el servidor tiene todas las versiones)+ (tienes todo en ambos sitios)-(necesitas mas recursos)
# GIT (SISTEMA DISTRIBUIDO)
- No almacena archivos que no han cambiado sino un enlace anterior 
- Lo almacena todo en local
## ESTADOS DE GIT  

- Sin seguimiento (UNTRACKED)
- En seguimiento (TRACKED)
- Modificado
- En Stage (PREPARADO) Indice que recoge la informacion sobre la proxima confirmacion
- Confirmado (COMMIT) Almacenado en la base de datos
## SECCIONES

- DIRECTORIO DE TRABAJO --> (Instantanea actual y archivos para modificar)
- DIRECTORIO GIT -->Almacena los metadatos y la base de datos 
- AREA DE PREPARADOS-->STAGE
# COMANDOS DE GIT HABITUALES
#### ESTADOS
Untracked (Lo has modificado)
Changes to be committed(esta en el stage)PDF_23
## COMIENZO 
``` 
git init --> Crea un repositorio de git y el directorio 
git clone https://github.com/[Nombre_Repositorio_Donde_lo_Guardara]
@ParametrosConfiguracion
git config --global user.name raul 
git config --global user.email raul 
git config --global editor.name raul 
git config --global core.editor nano
git config --list  -->MUESTRA LAS OPCIONES CONFIGURADAS
```
### AGREGAR AL STAGE Y HACER COMMIT 
git add Nombrearchivo  --> Manda al stage
git . --> manda todo al stage
git status --> Muestra el estado del stage

git commit                                      --> Abre el editor para el mensaje e introduce el commit 
git commit -m "mensaje texto"      --> haces commit con mensaje  
git commit -a -m "mensaje"          --> Te hace el git add y el git commit  a la vez
## ELIMINAR 
git rm NombreArchivo --> Borrar un archivo (DEBES AGREGARLO AL STAGE Y COMITEARLO)
## RENOMBRAR ARCHIVOS
git mv ArchivoViejo ArchivoNuevo
## IGNORAR ARCHIVOS

```
nano .gitignore (dentro le pones las extensiones que qiueres que bloquee) 
git add .gitignore 
git commit -m "ignorando con gitignore"
```
## LOGS
```
git log -->Historial de commits por defecto (Nombre autor,email,fecha,mensaje de commit)
--oneline -->Muestra simplificado (parte del checksum y el mensaje de commit)
--graph --> Crea un gráfico tipo árbol (en ASCII). 
-p -->Muestra las diferencias introducidas en cada commit
-numero -->Muestra los primeros commits que le digas   
```
## DESHACIENDO 

```
git commit --amend -->Corregir commit anterior añadiendo archivos olvidados y con add
git restore NombreArchivo --> Devuelve el archivo a como estaba en el ultimo commit
git restore --staged NombreArchivo --> Saca el archivo del stage   

git reset --soft --> Quita el ultimo commit sin cambiar nada y LO DEJA EN EL STAGE
git reset --mixed --> Quita el ultimo commit sin cambiar nada y SIN ESTAR EN STAGE
git reset --hard numeroHascomit--> Elimina todos los commits posteriores a este commit y deja el archivo como estaba en ese commit que indicas
```
## RAMAS
````
git branch --> Ves las ramas 
git branch -v --> Ves ramas y el commit de cada rama
git branch -d nombreRama --> eliminas la rama
```
```` 

### VER INFORMACION DE FUSION DE RAMAS
```
git branch --merged --> Muestra la rama actual y las ramas fusionadas a este
git branch -no--merged --> Muestra las ramas no fusionadas con la rama actual
```
### FUSION DE RAMAS(No se pierden commits)
git merge NombreRama--> Se une esta rama en la rama donde estas (Forma no lineal )
git rebase nombreRama -->Se une esta rama a donde estes de manera lineal (Forma lineal)
### GIT_SERVIDOR
SSH --> No permite conexiones anonimas
HTTP --> Permite accesos anonimos de lectura
GIT PROTOCOL --> no permite autenticarse (combiene solo lectura)
### REPOSITORIOS REMOTOS 
```
git pull --> Me descarga los archivos del remoto y si hemos modificado algo del mismo archivo las mismas lineas con cosas distintas te entra en conflicto y lo debees resolver.Una vez resuelto tienes los arhivos del respositorio y los tuyos
git push --> Subes tus archivos al repositorio y si hay conflicto lo modificas y lo cambias 
git fetch -->Descarga los archivos pero no los actualiza a los tuyos y si lo quieres fusionar haces un merge 
```
### VER REMOTOS 
```
git remote --> Mostrar los repositorios 
git remote -v --> Mostrar la direccion asociada
git remote show NOmbreRemoto-->Mostrar toda la informacion asociada a este remoto
```` 
### AÑADIR REMOTOS
 git remote add ``<shortname> <url>`` ---> Añadir un remoto
 git remote rename ``<old> <new>`` --> Renombrar un remoto
 git remote remove nombreRemoto --> Eliminar un remoto
### RECUPERAR INFO DEL REMOTO
git fetch NombreRemoto ``<nombreRamaDel_RepositorioRemotoQUeQuieresCojer>``  
git pull NombreRemoto ``<nombreRamaDel_RepositorioRemotoQUeQuieresCojer>`` 

### FLUJO  CENTRALIZADO (NO HAY RAMAS TODO A MAIN)

### GITHUBFLOW (VARIAS RAMAS PERO PRINCIPAL ES MAIN)
@VENTAJAS --> aisla a las funciones del desarrollados/Ramas respaldadas/Main sin errores
@DESVENTAJAS--> Aumentan los conflictos con merge de ramas de vida larga
### GITFLOW(Main oficial pero se trabaja en Develop)
- DEVELOP --> INTEGRA FUNCIONABILIDAD (feature ,hotfix)
@FEATURE -->Creas funcionalidades
@HOTFIX--> Errores
- RELEASE --> Version con posibles errores y cuando esta bien sale a MAIN
@MAIN --> Publicaciones oficiales

# TCP/IP y OSI 

## OSI  
- Aplicacion 
- Presentacion
- Sesion
- Transporte
- Network
- Data link
- Phisical
# TCP/IP 
- Aplicacion -->Interfaz (web - http)(email smtp )
- Transporte -->TCP (pierde paquetes)o UDP(no pierde paquetes)
- Red --> IP
- Enlace  -->Internet , wifi ,ADSL
5 --Si añades fisica --> si fibra o cable de telefono 

### DESPLIEGUE
- Instalar la aplicacion web que hemos desarrollado en un servidor web 
-VENTAJAS : Permite que la aplicacion siga funcionando aunque hayan muchas peticiones o falle algun host 
## ARQUITECTURAS
### P2P(TORRENT)
@VENTAJA
Haces de cliente y de servidor 
Facil escalabilidad
Costes mas economicos 
@DESVENTAJA
Dificil mantenimiento --> Porque no tiene un servidor centralizado
Poca fiabilidad -->No sabes de quien cojes el recurso (Poca seguridad)

### ARQUITECTURA DE 3 O MAS CAPAS 
@VENTAJA --> Puedes gestionar peticiones mas rapido ,+Escalable+fiable+seguridad

# SUBNETING 

IP --> Numeracion binaria que esta formada por 32 bits dividido en 4 bytes de 8bits cada uno 
BYTE -->La suma total de cada byte = 255

QUE ES UNA SUBRED ? 
- Es dividir una ip grande en mas pequeñas 
-@VENTAJAS 
Mas rendimiento 
Mas seguridad
Facilita la administracion de la red
Aprovecha mejor las direcciones ip 

2N=4                                                                                                                  4subredes

192.168.1.0/24        -à RED ACTUAL                                                                       

IIII IIII. IIII IIII. IIII IIII.0000 0000    à MASCARA  ACTUAL

255    .255.      255.         0              à MASCARA BINARIA

¿Cuántos bits hay que encender de host para 4 subredes?

|   |   |   |   |   |   |   |   |
|---|---|---|---|---|---|---|---|
|27|26|25|24|23|**22**|21|20|
|128|64|32|16|8|**4**|2|1|

2 bits hay que encender porque 2 elevado a 2 es igual a 4

**RESOLUCION** : 192.168.1.0/24+2=26

IIII IIII. IIII IIII. IIII IIII.1100 0000    à MASCARA  ACTUAL

255    .255.      255.        192          à MASCARA BINARIA

**HOST POR SUBRED** à 2**h** -2 (broadcast y red)

h= son los ceros que quedaron en la nueva mascara a la hora de hacer el cambio à 26 = 64 -2 = 62 host por subred

**SALTO DE RED** à256-192= 64 la red ira de 64 en 64

SALTO DE RED UTILIZABLE =62 en 62


# EJERCICIO

**

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|Dirección IP|Máscara|ID Networking|Dirección de difusión|Máscara de subred divida en 4 subredes|Intervalo de direcciones de host para la subred nº 3|
|129.102.197.23|255.255.0.0|129.102.0.0|129.102.255.255|255.255.192.0|129.102.128.1- 129.102.191.254|
|131.107.2.1|255.255.0.0|||||
|199.32.123.54|255.255.255.0|||||
|32.12.54.23|255.0.0.0|||||
|1.1.1.1|255.0.0.0|||||
|221.22.64.7|255.255.255.0|||||
|93.44.127.235|255.0.0.0|||||
|23.46.92.184|255.0.0.0|||||
|152.79.234.12|255.255.0.0|||||
|192.168.2.200|255.255.255.0|||||
|168.192.3.26|255.255.0.0|||||
|200.100.50.25|255.255.255.0|||||
|172.71.243.2|255.255.0.0|||||
|163.37.212.32|255.255.0.0|||||
|76.35.61.23|255.0.0.0|||||

  SSH --> 



















