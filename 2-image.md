# Imagen
Es un archivo único que contiene todos los programas, librerías, dependencias y configuraciones necesarias para instalar y/o ejecutar una aplicación o un conjunto de aplicaciones.
![Imagen](img/imagen.PNG)


## ¿Cuál es la relación entre una imagen y un contenedor? 
Imagen = Plantilla: La imagen es el "molde" a partir del cual se crean los contenedores.
Contenedor = Ejecución: El contenedor es una instancia viva de esa imagen, que corre de manera independiente.  
es decir que cuando ejecutamos un contenedor en docker se crean instancias (contenedor) a partir de una imagen ya existente (plantilla).

![Imagen y contenedores](img/imagenContenedores.JPG)
## Comandos para imágenes

### Descargar imagen
Descarga la última versión de la imagen disponible en el registro de Docker.

```
docker pull <nombre imagen> 
```

Descarga una versión específica de la imagen, cada imagen tiene etiquetas (tags) para diferentes versiones.
Una imagen puede tener la etiqueta latest para representar la última versión, si no se especifica una etiqueta se hará referencia a la versión latest.

```
docker pull <nombre imagen>:<tag>
```

Descargar la imagen **hello-world**
![Imagen Hello World](img/pullHello.png)

**¿Qué es nginx**
Nginx es un servidor web de alto rendimiento y un proxy inverso que también puede funcionar 
como balanceador de carga, proxy de correo electrónico y servidor de caché. 
Nginx utiliza un modelo de manejo de eventos asíncrono, lo que le permite manejar miles de conexiones 
simultáneamente con menos recursos que servidores como Apache, que usa un modelo de procesos o hilos para cada conexión.

Descargar la imagen  **nginx** en la versión **alpine**
![nginx](img/nginx.png)


### Listar imágenes

```
docker images
```

![Imagenes](img/dockerImages.png)

**Identificadores**

En Docker, se utilizan varios identificadores para diferenciar de manera única los elementos del sistema, como imágenes, contenedores, volúmenes y redes. Estos identificadores son generados automáticamente por Docker y son únicos dentro del contexto del sistema Docker en el que se encuentran. 

### Inspeccionar una imagen
El comando docker inspect se utiliza para obtener información detallada sobre un objeto de Docker específico, como un contenedor, una imagen, un volumen o una red.  Proporciona información en formato JSON sobre el objeto especificado.

```
docker inspect <nombre imagen>
docker inspect <nombre imagen>:<tag>
```

Inspeccionar la imagen hello-world 
![inspect](img/inspectHello.png)

**¿Con qué algoritmo se está generando el ID de la imagen**
SHA256 el cual es un algorimo de hash 

### Filtrar imágenes

```
docker images | grep <termino a buscar>

```

### Para eliminar una imagen
Eliminar permanentemente la imagen de tu sistema Docker.

```
docker rmi <nombre imagen>:<tag>
```

Eliminar la imagen hello-world 
![inspect](img/elminarImg.png)

-f: Es la opción para forzar la eliminación de la imagen incluso si hay contenedores en ejecución que utilizan esa imagen.
Cuando eliminas una imagen Docker, Docker no elimina automáticamente los contenedores que se han creado a partir de esa imagen. Esto significa que, aunque hayas eliminado la imagen, el contenedor seguirá ejecutándose normalmente.  
**Considerar**
Eliminar una imagen no afecta a los contenedores que se han creado a partir de esa imagen, a menos que esos contenedores dependan de archivos o configuraciones específicas de la imagen eliminada. En ese caso, es posible que los contenedores se comporten de manera inesperada después de eliminar la imagen.
Es una buena práctica detener y eliminar todos los contenedores que dependan de una imagen antes de eliminar la imagen en sí.

```
docker rmi -f <nombre imagen>:<tag>
```

