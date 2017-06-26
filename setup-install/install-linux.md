# Configuração e instalação de ambiente - Linux Ubuntu

### Instalando e configurando o `python`
1. __Instalação `python` e `pip`__
    
    O Python já vem pré-instalado nas distribuições Ubuntu do Linux.
    Verifique utilizando os comandos `python2 --version` e `python3 --version`
    
    Caso não tenha, instale com os comandos a seguir:
    ```shell
        #para o python 2
        sudo apt-get install python2
        
        #para o python 3
        sudo apt-get update
        sudo apt-get install python3
    ```
    
    Para fazer o upgrade do pip:
    ```shell
        #para python 2
        pip install -U pip
        
        #para python 3
        pip3 install -U pip
    ```
    
2. __Alteração do `$PATH`__

    Abra o arquivo bash com:
    ```shell
        vim ~/.bash_profile
    ```
    e adicione:
    ```shell
        export PATH=/usr/local/bin:$PATH
        test -f ~/.bashrc && source ~/.bashrc
    ```
    Salve e saia do arquivo vim. Em seguida, para aproveitar as alterações do bash na sessão atual do terminal, execute:
    ```shell
        source ~/.bash_profile
    ```
3. __Instalação e configuração de ambiente virtual__
    
    ```shell
        pip install virtualenv   #for python 2
        pip install venv         #for python 3
    ```
    Agora vamos criar diretórios para salvar os ambientes virtuais e arquivos de configuração:
    ```shell
        mkdir -p ~/Virtualenvs ~/Library/Application\ Support/pip
    ```
    Em seguida, abra o arquivo de configuração
    ```shell
        vim ~/Library/Application\ Support/pip/pip.conf
    ```
    E adicione:
    ```shell
        [install]
        require-virtualenv = true

        [uninstall]
        require-virtualenv = true
    ```
    com este passo você limita as instalações e desinstalações para apenas dentro dos ambientes virtuais, o que acaba evitando algumas dores de cabeça :D
    
    Agora é só criar o ambiente virtual com:
    ```shell
        cd ~/Virtualenvs
        virtualenv pytest2env                       #for Python 2
        python3 -m venv ~/Virtualenvs/pytest3env    #for Python 3
    ```
    Ative o ambiente virtual com: 
    ```shell
        cd pytest2env  #or pytest3env
        source bin/activate
    ```
    Agora que você está dentro do ambiente virtual você pode instalar qualquer biblioteca usando o pip.
    
    E desativar o ambiente com `deactivate`

### Clonando o repositório
No terminal, navegue até o diretório em que você deseja que fique o projeto e clone o repositório com:
```shell
    git clone https://github.com/izabelacborges/python-bootcamp-minicourse.git
```
E instale as dependencias com `pip install -r requirements.txt` dentro do ambiente virtual.

### PyCharm IDE
Se você quer a melhor IDE possível para um projeto python, e você não sabe deixar o Sublime/Atom hackudão, use o PyCharm :heart:. Você pode instalá-lo por [aqui](https://www.jetbrains.com/pycharm/download/).