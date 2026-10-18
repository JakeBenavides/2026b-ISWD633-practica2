# Limitar uso de procesador
Limitar la cantidad de núcleos de CPU:
```
--cpus=<número de núcleos>
```

Asignar núcleos de CPU específicos:
```
--cpuset-cpus=<lista de núcleos>
```

**¿Como saber el numero de procesadores virtuales que tiene una máquina?**
##### En este caso para poder saber el umero de procesadores que tiene la maquina podemos usar el comando ""$env:NUMBER_OF_PROCESSORS"
<img width="942" height="845" alt="image" src="https://github.com/user-attachments/assets/686761ce-29f0-4204-8fcc-300f28070d7e" />


## Ejemplos
_Puedes copiar y ejecutar directamente cada uno de los comandos_

Limitar el uso de CPU a 1.5 núcleos
```
docker run -d --name server-nginx --cpus="1.5" nginx:alpine
```
<img width="942" height="847" alt="image" src="https://github.com/user-attachments/assets/5e3a0b64-3959-49a6-be08-c29fd8fab99d" />


Restringir el contenedor para que use los núcleos de CPU 0 a 2:
```
docker run -d --name server-nginx --cpuset-cpus="0-2" nginx:alpine
```
<img width="935" height="851" alt="image" src="https://github.com/user-attachments/assets/76cdc39f-3471-478c-8ebb-3e8205b65704" />


Restringir el contenedor para que use los núcleos de CPU 1 y 3:
```
docker run -d --name server-nginx --cpuset-cpus="1,3" nginx:alpine
```
<img width="941" height="849" alt="image" src="https://github.com/user-attachments/assets/f29cae91-045f-4878-bead-29d8d122f99f" />

