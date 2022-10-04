# Geonode_Ime

Modelo de Projeto GeoNode. Gera um projeto django com suporte a GeoNode.

## Requisitos da Máquina
1. Sistema operacional Linux (Ubuntu, Debian, etc.) ou Subsistema Windows para Linux (no caso de uma máquina com Sistema operacional Windows);
2. Pip;
3. Python 3;
```bash
sudo apt update
sudo apt-get install python3-pip
```
5. Git;
```bash
sudo apt install git
```
7. Docker 1.12 ou versão superior;
```bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
sudo apt update
sudo apt install docker-ce
```

## Construir o servidor usando Docker

1. Preparar o ambiente de instalação

    ```bash
    ## Clonar o repositório
    git clone https://github.com/LinkestK/geonode_pfc_2.git -b main
    
    ## Criar ambiente virtual
    mkdir .virtualenv
    pip3 install virtualenv
    pip3 install virtualenvwrapper
    
    ## Alterar configurações do virtualenvwrapper
    export VIRTUALENVWRAPPER_PYTHON=/usr/bin/python3
    export WORKON_HOME=$HOME/.virtualenvs
    export VIRTUALENVWRAPPER_VIRTUALENV=/home/your_username/.local
    /bin/virtualenv
    source ~/.local/bin/virtualenvwrapper.sh 
    
    mkvirtualenv --python=/usr/bin/python3 geonode_ime
    pip install Django==2.2.15

    django-admin startproject --template=./geonode_pfc_2 -e py,sh,md,rst,json,yml,ini,env,sample,properties -n monitoring-cron -n Dockerfile geonode_ime

    cd geonode_ime
    ```

2. Executar `docker-compose` para iniciar (esse processo pode ser demorado)

    ```bash
    sudo docker-compose build --no-cache
    set COMPOSE_CONVERT_WINDOWS_PATHS=1
    sudo docker-compose up -d
    ```

   
3. Acesse o site do projeto no link: http://localhost/
