# Como instalar e usar o Docker no Windows 8

Obs: Se o seu sistema operacional for Linux, veja [como instalar o Docker no pingüim](https://github.com/llagerlof/today-i-learned/blob/master/2017-10-18_docker.md).

No Windows 8.0 e 8.1 você deve instalar o Docker Toolbox (e não o Docker for Windows, que é somente para o Windows 10).

Baixe o [Docker Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/). No momento da instalação desmarque os programas que você já tiver instalado no seu computador. Por exemplo, se você já tiver o git instalado e funcionando, desmarque-o. O mesmo vale para o VirtualBox. Se ele já estiver instalado, desmarque-o. O Kitematic é uma interface web para você gerenciar os containers. Não é obrigatório.

Após a instalação, verifique se o programa entrou no PATH do adminstrador do Windows. Se não entrou, insera ele no PATH. Verifique se o executável do docker está acessível abrindo o o cmd com poderes administrativos e digitando docker na linha de comando.

Crie a máquina virtual do Docker (necessário para que você possa acessar os serviços do Docker) com o comando:

```
docker-machine create default
```
Inicie a máquina virtual com o comando:

```
docker-machine start default
```

Feito isso você deve configurar algumas variáveis de ambiente. Para ver quais, digite:

```
docker-machine env default
```
Basta rodar todos os comandos SET exibidos. Não precisa executar as linhas que começam com REM.

Feito isso inicie o serviço com o comando:

```
docker-machine start default
```

Se tudo deu certo, seu ambiente já deve estar configurado e pronto pra usaro docker.

**Alguns comandos úteis:**

Para listar as máquinas virtuais do docker:

**IMPORTANTE**: No Windows 8 você não poderá usar o localhost para acessar os seus containers (no Linux você pode). O IP que você deve usar quando quiser acessar algum serviço nos seus containers é o que aparece quando você executa esse comando:

```
docker-machine ls
```

Para parar a máquina virtual do docker (lembrando que o nome que nós usamos para criar ela foi "default"):

```
docker-machine stop default
```

## Criando uma aplicação PHP de exemplo

Crie um diretório vazio e entre nele. Crie dois arquivos:
  * Dockerfile
  * index.php

No **Dockerfile** coloque o conteúdo abaixo:
```
# Define que a imagem a ser usada é a "php" do repositório do Docker. Ela será baixada quando você executar o build logo abaixo.
FROM php

# Instala no container o apt-utils.
RUN apt-get update && apt-get install -y apt-utils

# Instala no container as bibliotecas do MySQL para o PHP.
RUN apt-get update && apt-get install -y libmysqlclient-dev && docker-php-ext-install -j$(nproc) pdo_mysql

# Define o diretório /app como o atual no container.
WORKDIR /app

# Serve somente para documentar a porta que este container libera.
EXPOSE 80

# Copia os arquivos do diretório atual do host para o diretório /app do container.
ADD . /app

# Roda o servidor http embutido do PHP.
CMD ["php", "-S", "0.0.0.0:80"]
```

No **index.php** coloque o conteúdo abaixo:
```
<?php
    phpinfo();
?>
```

Faça o build do container:
```
$ docker build -t phpapp .
```

Rode o container:
```
$ docker run -d -p 4000:80 phpapp
```

No seu navegador acesse a porta 4000 da máquina onde o Docker está rodando para acessar a porta 80 do container, usando o seu navegador. O IP que você deve usar é o que aparece quando você executa o comando ```docker-machine ls```

http://ip_retornado_pelo_comando_docker_machine_ls:4000/index.php


## Como montar um diretório do host dentro do container.

**Crie um volume:**

```
$ docker volume create storage01
```

**Inicie o container indicando qual volume vai usar e em qual diretório do container vai monta-lo:**

```
$ docker run -p 4000:80 --mount source=storage01,target=/app/st01 phpapp
```

No exemplo acima a sua aplicação pode ler e escrever no diretório /app/st01, que na verdade estará estará manipulando o conteúdo do diretório do container. Para saber que diretório é esse, digite:

```
$ docker volume ls
$ docker volume inspect storage01
```

# Notas

**Listar as imagens disponíveis:**
```
$ docker images
```

**Listar os containers que estão em execução:**
```
$ docker container ls
```

**Ajuda:**
```
$ docker
```

**Repositório online de imagens do Docker:**

https://hub.docker.com/explore/

---

*keywords: docker, container, installation, install, run, linux, image, imagem, tutorial*

*references:*

*https://docs.docker.com/get-started/#setup*

*https://docs.docker.com/engine/installation/linux/linux-postinstall/#configure-docker-to-start-on-boot*

*https://docs.docker.com/engine/installation/linux/docker-ce/debian/#install-using-the-repository*

*https://docs.docker.com/engine/reference/run/*

*https://docs.docker.com/engine/installation/linux/docker-ce/centos/#install-using-the-repository*

*https://github.com/moby/moby/pull/21032*
