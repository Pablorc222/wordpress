# Instalación de Wordpress en arquitectura de 3/4 capas en alta disponibilidad.

# Índice.

1. [Introducción.](#introducción)
2. [Infraestructura.](#infraestructura)
3. [Provisionamiento de las máquinas.](provisionamiento_de_las_máquinas) 
    * [Balanceador.](#balanceador)
    * [Servidor web 1.](#servidor-web-1)
    * [Servidor web 2.](#servidor-web-2)
    * [Servidor NFS y motor PHP.](#servidor-nfs-y-motor-php)
    * [Balanceador BBDD.](#balanceador-bbdd)
4. [Screencash](#screencash)

# Introducción


En esta práctica, se implementa un despliegue automático de un CMS WordPress en una infraestructura con cuatro capas. 
A continuación, se describen brevemente las características de cada capa:

    * Capa de Balanceo de Carga (Capa 1):
Contiene un balanceador de carga que distribuye las solicitudes entre los servidores web.
El balanceador de carga en esta capa tiene acceso a Internet.

    * Capa de BackEnd (Capa 2):
Incluye servidores de BackEnd que constan de dos servidores web y un servidor NFS y PHP.

    * Capa de Balanceo de Carga para Bases de Datos (Capa 3):
Tiene un balanceador de carga que distribuye las solicitudes entre los servidores de bases de datos.

    * Capa de Clúster de Base de Datos (Capa 4):
Forma un clúster de bases de datos compuesto por dos servidores.

Además, se establece la restricción de conexión para cada máquina, limitando el acceso a su propia red. 
La excepción es el balanceador de carga de la Capa 1, que tiene acceso a Internet, 
probablemente para gestionar las solicitudes externas.
