# Políticas de reinicio

## Para esta parte de la práctica
1. Usa el archivo Dockerfile que se encuentra en cada carpeta con el nombre de la política de reinicio para crear una imagen. Analiza las instrucciones de cada Dockerfile 
2. Usa la imagen para ejecutar un contenedor agregando la política respectiva y observar lo que sucede verificando el cumplimiento de la política de reinicio

<img width="939" height="850" alt="image" src="https://github.com/user-attachments/assets/ab085d17-69b7-4298-9d14-ebe83c6c6473" />

docker build -t img-no ./no
docker build -t img-always ./always
docker build -t img-unless ./unless-stopped
docker build -t img-onfailure ./on-failure

### no
No reinicia el contenedor bajo ninguna razón. Esta es la política por default
```
docker run -d --name c-no img-no
```
##### Solo tiene FROM centos:8, sin script. Al arrancar, el contenedor termina de inmediato con código 0.
<img width="935" height="843" alt="image" src="https://github.com/user-attachments/assets/03cd91a2-e35a-4503-9647-17f12a91c757" />


### always
Reinicia siempre el contenedor si se detiene. Si se detiene manualmente, sólo se reiniciará cuando se reinicie el demonio Docker o cuando se reinicie manualmente el propio contenedor
```
docker run -d --name c-always --restart always img-always
```
##### opian inicio.sh, le dan permisos con chmod +x y lo ejecutan con CMD. El script imprime mensajes, espera 6 segundos y termina con exit 1 (código de error).

### unless-stopped

Similar a always, excepto que cuando el contenedor se detiene (manualmente o de otra manera), no se reinicia incluso después de reiniciar el demonio Docker.
```
docker run -d --name c-unless --restart unless-stopped img-unless
```

### on-failure
Se reinicia únicamente cuando hay una falla en la ejecución del código que se manifiesta con un código diferente de 0. No se reinicia si el contenedor se detiene manualmente.

##### copian inicio.sh, le dan permisos con chmod +x y lo ejecutan con CMD. El script imprime mensajes, espera 6 segundos y termina con exit 1 (código de error).
```
docker run -d --name c-onfailure --restart on-failure img-onfailure
```
