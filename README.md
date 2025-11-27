# Servidor Palworld com Docker no Ubuntu (Google Cloud)

Este guia mostra como instalar e configurar um servidor Palworld
dedicado usando Docker no Ubuntu.\
Compatível com Google Cloud e outras plataformas baseadas em Ubuntu.

------------------------------------------------------------------------

## ✔ Recursos do Tutorial

-   Instalação completa do Docker e Docker Compose
-   Configuração rápida do arquivo docker-compose.yml
-   Comandos organizados e prontos para copiar
-   Estrutura otimizada para iniciantes e avançados

------------------------------------------------------------------------

## 🖥 Requisitos

-   Ubuntu 20.04 ou superior\
-   Acesso root ou usuário com sudo\
-   Máquina virtual com portas liberadas (caso vá jogar online)
-   Porta 8211 Liberada

------------------------------------------------------------------------

## 1. Acessar como root

    sudo su

## 2. Atualizar o sistema

    sudo apt update
    sudo apt upgrade -y

## 3. Instalar dependências do Docker

    sudo apt update
    sudo apt install ca-certificates curl -y
    sudo install -m 0755 -d /etc/apt/keyrings
    sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
    sudo chmod a+r /etc/apt/keyrings/docker.asc

## 4. Adicionar repositório oficial do Docker

    sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
    Types: deb
    URIs: https://download.docker.com/linux/ubuntu
    Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
    Components: stable
    Signed-By: /etc/apt/keyrings/docker.asc
    EOF

## 5. Instalar Docker e Docker Compose

    sudo apt update
    sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y

## 6. Verificar instalação

    sudo docker --version
    docker compose version

------------------------------------------------------------------------

## 7. Criar o arquivo docker-compose.yml

Instalar o nano caso necessário:

    sudo apt install nano -y

Criar o arquivo:

    sudo nano docker-compose.yml

Criar o .env:

    sudo nano .env

------------------------------------------------------------------------

## 8. Iniciar o servidor Palworld

    sudo docker compose up

Ver logs:

    docker compose logs

Parar o servidor:

    docker compose down

------------------------------------------------------------------------

## 📌 Observações importantes

-   Certifique-se de liberar portas no firewall da Google Cloud.
-   Mantenha sempre backups do servidor.
-   Atualize a imagem Docker periodicamente.

------------------------------------------------------------------------

## 📄 Licença

Este projeto é livre para uso e modificação.
