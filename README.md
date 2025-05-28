# 🛠️ Demos de Uso de Docker
![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)
- Demostraciones prácticas que muestran cómo utilizar Docker en diferentes escenarios.

## 📂 Contenido
### Dockerfile
- [Imagen de contenedor con Amazon Linux 2023](https://github.com/samuelrojasm/demo-docker/tree/main/dockerfile-examples/amazonlinux2023-demo)
- [Amazon Linux 2023 + Python](https://github.com/samuelrojasm/demo-docker/tree/main/dockerfile-examples/amazonlinux2023-python)

### Docker CLI
- [Presistencia de datos - bind mount](https://github.com/samuelrojasm/demo-docker/tree/main/data-management/persistencia-datos)

---

## Conceptos Clave
- **Contenedores**: Un contenedor es una instancia en ejecución de una imagen Docker.
- **Dockerfile**: Archivo de texto con instrucciones para crear una imagen Docker personalizada.
- **Docker Compose**: Herramienta para definir y ejecutar aplicaciones Docker multicontenedor.

---

## Ejemplos de comandos de Docker

```zsh
# Obtener imagen minimalista de Amazon Linux
docker pull public.ecr.aws/amazonlinux/amazonlinux:2023-minimal
```

```zsh
# Usar el digest SHA directamente garantiza que siempre es la misma imagen
docker pull public.ecr.aws/amazonlinux/amazonlinux@sha256:<digest>
```

```zsh
# Obtener el digest SHA
docker inspect \
    public.ecr.aws/amazonlinux/amazonlinux:2023 \ # Nombre completo de la imagen
    --format '{{ .RepoDigests }}'                 # Filtro usando plantilla Go con propiedad del objeto de salida (JSON)
```

```zsh
# Buscar el digest SHA más reciente
docker pull public.ecr.aws/amazonlinux/amazonlinux:2023
docker inspect public.ecr.aws/amazonlinux/amazonlinux:2023 --format '{{ index .RepoDigests 0 }}'
```

```zsh
# Ejecutar contenedor interactivo
docker run \ 
  -it \                       # Terminal interactiva dentro del contenedor (-i para input interactivo, -t para emular un pseudo-TTY).
  mi-imagen-amazonlinux2023 \ # Imagen a ejecutar
  bash                        # Abre una shell dentro del contenedor
```

```zsh
# Asignamos un nombre personalizado al contendor
# Al salir con exit o Ctrl+D, detendrá el contenedor pero no lo eliminará
docker run -it --name mi-contenedor-al2023 mi-imagen-amazonlinux2023 bash
```

```zsh
# Reanudar sesión en el contenedor
docker start \ 
   -ai  \ -a: adjunta la terminal a la salida -i: habilita la entrada interactiva
   mi-contenedor-al2023
```

```zsh
# Eliminar el contenedor cuando ya no se necesite
docker rm mi-contenedor-al2023
```

```zsh
# Eliminar la imagen (si ya no se necesita)
docker rmi mi-imagen-amazonlinux2023
```

```zsh
# Ejecutar contenedor interactivo y efímero
docker run \
  --rm \          # Borrar contenedor al salir, no quedará listado ni siquiera con docker container ls -a.
  -it \           # Terminal interactiva dentro del contenedor (-i para input interactivo, -t para emular un pseudo-TTY).
  mi-imagen       # Imagen a ejecutar
```

```zsh
# Al salir con exit o Ctrl+D, el contenedor:
# Se detiene, es eliminado inmediatamente, no aparece al listar contenedores detenidos
docker run --rm -it mi-imagen-amazonlinux2023 bash
```

```zsh
# Ver y comparar los paquetes instalados
docker run --rm -it public.ecr.aws/amazonlinux/amazonlinux:2023-minimal rpm -qa
```

```zsh
#  Obtener tamaño real expandido de la imagen
 docker run --rm -it public.ecr.aws/amazonlinux/amazonlinux:2023 du -sh /
```

```zsh
 # Mostrar solo la arquitectura (amd64, arm64, etc.) de una imagen específica
docker image inspect \
  public.ecr.aws/amazonlinux/amazonlinux:2023 \  # Nombre completo de la imagen
  --format '{{ .Architecture }}'                 # Filtro usando plantilla Go con propiedad del objeto de salida (JSON)
```

```zsh
# Correr contenedor y verificar arquitectura desde dentro
docker run --rm -it public.ecr.aws/amazonlinux/amazonlinux:2023 uname -m
```

```zsh
# Consultar el manifiesto para la etiqueta 2023
docker manifest inspect public.ecr.aws/amazonlinux/amazonlinux:2023
```

---

## Requisitos previos
- [Docker](https://www.docker.com/get-started) (Instalar la versión más reciente)
- [Docker Compose](https://docs.docker.com/compose/install/)

---