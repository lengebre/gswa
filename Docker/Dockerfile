FROM ubuntu:focal
WORKDIR /usr/local/bin
ARG DEBIAN_FRONTEND=noninteractive
# https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-ansible-on-ubuntu
RUN apt update  \ 
    && apt install -y software-properties-common \
    && apt-add-repository -y ppa:ansible/ansible \
    && apt install -y curl git ansible build-essential \
    && apt install -y python3-pip \
    && pip install "ansible-lint[yamllint]"
COPY ./playbook ./playbook
# CMD ["sh", "-c", "ansible-playbook git_config.yml"]

# docker build . -t gswa  
# docker run -it --rm gswa /bin/bash        