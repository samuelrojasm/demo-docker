# Usar Amazon Linux 2023 como base
FROM public.ecr.aws/amazonlinux/amazonlinux:2023

# Actualizar e instalar paquetes necesarios
RUN yum update -y && \
    yum install -y \
    unzip \
    tar \
    git \
    && yum clean all

# Crear un usuario no root (opcional)
RUN useradd -m appuser
USER appuser

# Establecer el directorio de trabajo
WORKDIR /home/appuser/app

# Copiar archivos (por ejemplo, una app)
# COPY . .

# Comando por defecto
CMD ["bash"]