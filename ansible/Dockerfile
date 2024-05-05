# Definimos el sistema operativo que vamos a usar
FROM python:3.8

# Instalamos nano y otras dependencias si es necesario
RUN apt-get update && \
    apt-get install -y nano

# Copiamos los tres archivos YAML (install.yaml, create_env.yml, execute_script.yml)
# y el script Python con el mensaje "Hola" al contenedor
COPY playbooks/ /ansible/playbooks/
COPY mensaje.py /ansible/

# Definimos el directorio de trabajo
WORKDIR /ansible

# Instalamos Ansible dentro del contenedor
RUN pip install ansible

# Ejecutar los tres playbooks de Ansible
CMD ansible-playbook playbooks/install.yaml && \
    ansible-playbook playbooks/create_env.yml && \
    ansible-playbook playbooks/execute_script.yml
