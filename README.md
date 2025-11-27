# 🐦 Palworld Dedicated Server no Ubuntu (Google Cloud, AWS ou Hostinger)

Este guia foi criado para acompanhar meu vídeo tutorial mostrando como criar seu próprio servidor dedicado de Palworld rodando 24 horas por dia. O processo funciona em **[Google Cloud](https://console.cloud.google.com/)**, **[AWS](https://aws.amazon.com/pt/free/)** e **[Hostinger VPS](https://hostinger.com.br?REFERRALCODE=AUABMGREYCIA)** 

A instalação abaixo é focada em **Ubuntu** e usa o projeto **[oficial](https://github.com/thijsvanloef/palworld-server-docker)** do Palworld Server em Docker:
[GitHub Oficial Palworld Dedicated Server Docker](https://github.com/thijsvanloef/palworld-server-docker)


## 🖥 Requisitos

- Ubuntu 20.04 ou superior  
- Acesso root ou usuário com sudo  
- Máquina virtual com portas liberadas  
- Porta 8211 aberta no firewall (necessária para o jogo)

---

## 1. Acessar como root

    sudo su

## 2. Atualizar o sistema

    sudo apt update
    sudo apt upgrade -y

---

## 3. Instalar o Docker

Siga as instruções oficiais do Docker para instalar corretamente:

- Instalação do Docker Engine:  
  https://docs.docker.com/engine/install/

Links diretos para distros suportadas:
- [Ubuntu](https://docs.docker.com/engine/install/ubuntu/)
- [Debian](https://docs.docker.com/engine/install/debian/)
- [CentOS](https://docs.docker.com/engine/install/centos/)
- [Raspberry Pi OS](https://docs.docker.com/engine/install/raspberry-pi-os/)

---


## 4. Verificar instalação

    sudo docker --version
    docker compose version

---

## 5. Criar o arquivo docker-compose.yml

Instale o nano se necessário:

    sudo apt install nano -y

Crie o arquivo principal:

    sudo nano docker-compose.yml

Cole dentro dele o conteúdo fornecido do  [repositório oficial](https://github.com/thijsvanloef/palworld-server-docker/tree/main?tab=readme-ov-file) abaixo.
    
```yml
services:
   palworld:
      image: thijsvanloef/palworld-server-docker:latest
      restart: unless-stopped
      container_name: palworld-server
      stop_grace_period: 30s # Set to however long you are willing to wait for the container to gracefully stop
      ports:
        - 8211:8211/udp
        - 27015:27015/udp
        # - 8212:8212/tcp  # Port for REST API if REST_API_ENABLED: true
      env_file:
         -  .env
      volumes:
         - ./palworld:/palworld/
```

---

## 6. Criar o arquivo .env

    sudo nano .env

Preencha com as variáveis oficiais do projeto, copiadas [.env.example](.env.example).

---

## 7. Iniciar o servidor Palworld

    sudo docker compose up

Ver logs:

    docker compose logs

Parar o servidor:

    docker compose down

---

Lembre-se: caso queira ver **todos os comandos completos**, configurações avançadas e parâmetros adicionais, consulte o repositório oficial: https://github.com/thijsvanloef/palworld-server-docker

