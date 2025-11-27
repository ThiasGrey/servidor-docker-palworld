# 🐦 Palworld Dedicated Server no Ubuntu (Google Cloud, AWS ou Hostinger)

Este guia foi criado para acompanhar meu vídeo tutorial mostrando como criar seu próprio servidor dedicado de Palworld rodando 24 horas por dia. O processo funciona em **Google Cloud**, **AWS** e **Hostinger VPS** (inclusive recomendo a Hostinger por ser mais simples e barata: https://hostinger.com.br?REFERRALCODE=AUABMGREYCIA).

A instalação abaixo é focada em **Ubuntu** e usa o projeto **oficial** do Palworld Server em Docker:

GitHub Oficial com comandos completos:  
https://github.com/thijsvanloef/palworld-server-docker/tree/main?tab=readme-ov-file

---

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
- Ubuntu: https://docs.docker.com/engine/install/ubuntu/
- Debian: https://docs.docker.com/engine/install/debian/
- CentOS: https://docs.docker.com/engine/install/centos/
- Raspberry Pi OS: https://docs.docker.com/engine/install/raspberry-pi-os/

---

## 4. Instalar Docker e Docker Compose

    sudo apt update
    sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y

## 5. Verificar instalação

    sudo docker --version
    docker compose version

---

## 6. Criar o arquivo docker-compose.yml

Instale o nano se necessário:

    sudo apt install nano -y

Crie o arquivo principal:

    sudo nano docker-compose.yml

Cole dentro dele o conteúdo fornecido no repositório oficial acima.

---

## 7. Criar o arquivo .env

    sudo nano .env

Preencha com as variáveis oficiais do projeto, copiadas diretamente do GitHub.

---

## 8. Iniciar o servidor Palworld

    sudo docker compose up

Ver logs:

    docker compose logs

Parar o servidor:

    docker compose down

---

Lembre-se: caso queira ver **todos os comandos completos**, configurações avançadas e parâmetros adicionais, consulte o repositório oficial:
https://github.com/thijsvanloef/palworld-server-docker/tree/main?tab=readme-ov-file

