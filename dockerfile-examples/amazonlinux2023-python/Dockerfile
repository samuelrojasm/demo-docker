# Usar la imagen oficial de Amazon Linux 2023 como base
FROM public.ecr.aws/amazonlinux/amazonlinux:2023

# Establecer el directorio de trabajo
WORKDIR /app

# Instalar actualizaciones y paquetes necesarios (ejemplo: Python)
RUN dnf update -y && \
    dnf install -y python3 python3-pip && \
    dnf clean all

# Copiar archivos de la app al contenedor
COPY . /app

# Comando por defecto
CMD ["python3", "--version"]