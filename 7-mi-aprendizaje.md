# COMPLETAR  
Comparando sus conocimientos antes de hacer la práctica con sus conocimientos después de hacer la tarea, explicar los principales aprendizajes logrados para beneficio de su formación profesional.  
Si solucionó un problema presentado al realizar la práctica también se debe documentar.


Antes de hacer esto sabía crear y ejecutar contenedores, pero no que se les podían poner límites ni que Docker podía vigilar su estado de salud. Lo primero que aprendí es que Docker no usa megabytes de 1000 sino de 1024, por eso al limitar la memoria con --memory=300m --memory-swap=1g el swap disponible es de 724 MB y no de 700. También entendí que existen dos tipos de memoria, la RAM y la swap, y que --memory-swap solo funciona junto con --memory, porque es el total de ambas y la swap no sirve sin la RAM. Además vi que se puede limitar el procesador con --cpus o elegir qué núcleos usar con --cpuset-cpus. Lo que más entendí fue el healthcheck, porque permite saber el estado de salud de un contenedor, que puede estar en ejecución y aun así no funcionar bien. 

Durante la práctica tuve algunos problemas. Al construir la imagen con CentOS 7, yum update falló porque sus repositorios ya no existen, y lo solucioné cambiándolos a vault.centos.org con un sed. El contenedor de nginx aparecía como unhealthy porque la imagen no trae curl, así que usé wget en el healthcheck. 
