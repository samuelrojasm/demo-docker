# Demo: Archivos en Docker

- Demostración de cómo trabajar con contenedores Docker, específicamente enfocándose en la creación y gestión de archivos dentro de un contenedor utilizando un bind mount.

- Este ejemplo utiliza un **bind mount**, lo que significa que los archivos creados dentro del contenedor se reflejan directamente en el sistema de archivos del host.

- No se crean volúmenes de Docker en este proceso, ya que se está utilizando un **bind mount**.

---

## Objetivo

El objetivo de esta demostración es mostrar cómo ejecutar un contenedor de Docker, crear archivos dentro de él y verificar la persistencia de esos archivos en el sistema de archivos del host.

--

## Requisitos

- Docker instalado.
- Acceso a la terminal.

---

## Pasos

### 1. Ejecutar un contenedor en modo desapegado (detached mode)

Ejecuta un contenedor a partir de la imagen `alpine:3.17`, montando el directorio `/tmp/docker/storage` de la máquina host en el directorio `/home` del contenedor.

```bash
docker run -d --name my_alpine_container -v /tmp/docker/storage:/home alpine:3.17 tail -f /dev/null
```

### Paso 2: Crear archivos dentro del contenedor
```bash
docker exec -it my_alpine_container sh -c "echo 'Contenido archivo01' > /home/archivo01 && echo 'Contenido archivo02' > /home/archivo02"
```

### Paso 3: Verificar archivos en el host
```bash
ls /tmp/docker/storage
```

# Eliminar archivo01
```bash
rm /tmp/docker/storage/archivo01
```

# Entrar nuevamente al contenedor
```bash
docker exec -it my_alpine_container sh
```

# Verificar archivos dentro del contenedor
```bash
ls /home
```

# Paso 4: Verificar volúmenes
```bash
docker volume ls
```
