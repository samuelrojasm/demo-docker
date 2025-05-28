# 🛠️ Demo: Archivos en Docker
![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)

- Demostración de cómo trabajar con contenedores Docker, específicamente enfocándose en la creación y gestión de archivos dentro de un contenedor utilizando un bind mount.
- Este ejemplo utiliza un **bind mount**, lo que significa que los archivos creados dentro del contenedor se reflejan directamente en el sistema de archivos del host.
- No se crean volúmenes de Docker en este proceso, ya que se está utilizando un **bind mount**.

---

## 🎯 Objetivo (Target)

El objetivo de esta demostración es mostrar cómo ejecutar un contenedor de Docker, crear archivos dentro de él y verificar la persistencia de esos archivos en el sistema de archivos del host.

---

## ✅ Requisitos

- Docker instalado.
- Acceso a la terminal.

### Nota: uso de Podman en MacOS
- En MacOS, **podman** usa una máquina virtual en **podman machine**.
- Por lo tanto, la carpeta /tmp/docker/storage debe existir dentro de la VM de Podman, no solo en la Mac.
- Podman permite configurar volúmenes al crear la VM (**podman machine**)
```bash
mkdir -p /tmp/docker/storage
podman machine init --volume /tmp/docker/storage:/tmp/docker/storage
podman machine start
```
---

## 🚀 Pasos

### 1. Ejecutar un contenedor en modo desapegado (detached mode)

- Ejecuta un contenedor a partir de la imagen `alpine:3.17`, montando el directorio `/tmp/docker/storage` de la máquina host en el directorio `/home` del contenedor.

- Opción 1: usando -v
```bash
docker run -d -t --name nuevo_contenedor_alpine -v /tmp/docker/storage:/home alpine:3.17
```
- Opción 2: usando --mount
```bash
docker run -d -t --name otro-contenedor-alpine --mount type=bind,src=/tmp/docker/storage,dst=/home alpine:3.17
```
---

### 2. Crear archivos dentro del contenedor
```bash
docker exec -it nuevo_contenedor_alpine sh -c "echo 'Contenido archivo01' > /home/archivo01 && echo 'Contenido archivo02' > /home/archivo02"
```
---

### 3. Verificar archivos en el host
```bash
ls /tmp/docker/storage
```

#### Eliminar archivo01
```bash
rm /tmp/docker/storage/archivo01
```

#### Entrar nuevamente al contenedor
```bash
docker exec -it nuevo_contenedor_alpine sh
```

#### Verificar archivos dentro del contenedor
```bash
ls /home
```
---

### 4. Verificar volúmenes
```bash
docker volume ls
```
