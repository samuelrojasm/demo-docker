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

- Ejecutar contenedor:
```bash
docker run --rm -it mi-imagen-amazonlinux2023
```

- obtener la imagen minimalista más reciente con el siguiente comando:
```bash
docker pull public.ecr.aws/amazonlinux/amazonlinux:2023-minimal
```




---

## Requisitos previos
- [Docker](https://www.docker.com/get-started) (Instalar la versión más reciente)
- [Docker Compose](https://docs.docker.com/compose/install/)

---