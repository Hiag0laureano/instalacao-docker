# Instalação do Docker Desktop no Linux Ubuntu 22.04
## A instalação foi feita em uma máquina virtual usando o VirtualBox
### VirtualBox
    VirtualBox é um software de virtualização desenvolvido pela empresa Innotek depois comprado pela Sun Microsystems que posteriormente foi comprada pela Oracle que, como o VMware Workstation, visa criar ambientes para instalação de sistemas distintos. 

    https://download.virtualbox.org/virtualbox/6.1.36/VirtualBox-6.1.36-152435-Win.exe

    ### Após a instalação e criação da máquina Virtual para o sistema Ubuntu,  você deve acessar as configuração da maquina, ir ao item sistema, clicar na guia processador e habilitar "habilitar VT-x/AMD-V alinhado".

### Linux Ubuntu 22.04
    Ubuntu é um sistema operacional ou sistema operativo de código aberto, construído a partir do núcleo Linux, baseado no Debian e utiliza GNOME como ambiente de desktop de sua mais recente versão com suporte de longo prazo. Esta distribuição Linux é desenvolvida pela Canonical Ltd. 

    https://ubuntu.com/download/desktop

### Docker
    Docker é um conjunto de produtos de plataforma como serviço que usam virtualização de nível de sistema operacional para entregar software em pacotes chamados contêineres. Os contêineres são isolados uns dos outros e agrupam seus próprios softwares, bibliotecas e arquivos de configuração.

## Configuração e instalação de ambiente

### Pós-instalação do Linux 
    Após a instalação do Linux ubuntu 20.04, você deve execultar alguns comandos para utilizar o sistema e deixa-lo preparando para a instalação do docker.

    ### Atualização dos pacotes
        ```console
        $ sudo apt update
        ```

    ### Atualização do sistema
        ```console
        $ sudo apt upgrade
        ```

    ### Reinicie o sistema
        ```console
        $ reboot
        ```
### Instalação do Docker desktop 

    Download do docker desktop

    https://desktop.docker.com/linux/main/amd64/docker-desktop-4.10.1-amd64.deb?utm_source=docker&utm_medium=webreferral&utm_campaign=docs-driven-download-linux-amd64

    Na pasta(diretório) download localize o arquivo deocker-desktop-4.10.1-amd64
    deb e assim você pode instalar de duas maneiras, sendo:
     1º - Clicar com o botão direito do mouse sobre o arquivo e escolher o Software Install.

     2º - Abrir o terminal e ir até a pasta(diretório) download e execultar o comando de instalação:
        ```console
            $ sudo apt install ./docker-desktop-4.10.1-amd64.deb
        ```
    ### Caso retorne menssagem de erro referente ao docker-ce e/ou docker-cli, execultae os comando abaixo:
        ```console
            $ sudo sudo apt-get update

            $ sudo apt-get install \
                ca-certificates \
                curl \
                gnupg \
                lsb-release
        ```
        Adicionar as chaves de GPG oficiais do docker
            ```console
                $ sudo mkdir -p /etc/apt/keyrings
                $ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
            ```
        Use os comando abaixos para carregar o repositorio de pacotes
            ```console
                $ echo \
                "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
                $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
            ```
        ### Instalação do Docker Engine
            ```console
                $ sudo apt-get update
                $ sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
            ```
### Após a instalação das dependecias você deve execultar o comando de instalação do docker desktop
    ```console
        $ sudo apt install ./docker-desktop-4.10.1-amd64.deb
    ```
## Instalando a Imagem e o Container de MySQL no docker
### Vamos usar volume neste exemplo
    Crie uma pasta(diretório) chamada data_docker, no home do usuário, execulte o seguinte comando:
        ```console
           $ docker run --name servidor-mysql -v ~/data_docker:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=hiago123 -d mysql:8.0.29
       ```
    Agora, abra o docker-desktop e veja o seu container rodando.