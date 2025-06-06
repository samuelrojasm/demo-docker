## 🛠️ Demo: Imagen de contenedor con Amazon Linux 2023
![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)

## 🎯 Objetivo (Target)
Crear una imagen de contenedor con **Amazon Linux 2023**, usa un **Dockerfile** simple basado en la imagen oficial de Amazon Linux 2023 que ya está disponible en **Amazon ECR Public Gallery**

---

## Pasos para contruir la imagen
### 1.- Crear Imagen: Ejecutar en el mismo directorio del archivo dockerfile
```bash
docker build -t amazonlinux2023-demo .
```

### 2.- Correr contenedor
```bash
docker run -it amazonlinux2023-demo
```

## 🚀 Resultado (Outcome)
### Ejecución de contendor
 <p align="center">
    <img src="assets/imagenes/contenedor_amazonlinux2023.png" alt="Storage Account" width="70%">
</p>

---

## 📚 Referencias
- [Amazon ECR Public Gallery](https://gallery.ecr.aws/amazonlinux/amazonlinux)
- [Amazon Linux 2023 FAQs](https://aws.amazon.com/linux/amazon-linux-2023/faqs/)

---