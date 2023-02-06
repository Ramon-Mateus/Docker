# Docker & Docker-Compose

- A infraestrutura desenvolvida foi a de a simulação de um sistema em node que utiliza como banco de dados o mysql.

- Foi configurado dois containers. Um com o node.js e outro com o mysql. Ambos configurados com o docker compose. Além disso, foram criados volumes que faz refletir mudanças nos dois sentidos. Tanto do container para a sua máquina, quanto o inverso.

# Comandos úteis

* Caso não exista a imagem em questão no seu computador, ele baixa, roda e depois ou morre ou fica em foreground no seu terminal, pois por padrão ele não coloca em modo  background.

```shell
  docker run {nome da imagem}
```

* Roda o container em modo background.

```shell
  docker run -d {nome da imagem}
```

* Faz com que quando o container rodar e subir na porta 80, encaminhar para o navegador na porta 8000. Pois a porta 80 só vai rodar dentro do próprio container. Não externamente que é o caso do navegador do sistema operacional da sua máquina.

```shell
  docker run -p 8000:80 {nome da imagem}
```

* Esse comando faz você entrar no container e fazer a alteração que quiser dentro dos arquivos interno dele.

```shell
  docker exec -it {id container} {nome terminal (exemplo: sh, bash, zsh, …) }
```

* Mata o container, parando a sua execução.

```shell
  docker stop {id container}
```

* Apaga da máquina containers parados.

```shell
  docker rm {id container}
```

* Apaga a imagem da máquina.

```shell
  docker rmi {id da imagem}
```

* Para todos os containers ativos.

```shell
  docker stop $(docker ps -a -q)
```

* Roda um container passando o diretório atual (pwd) como volume para a pasta que está especificada no “caminho do container”.

```shell
  docker run -v $(pwd):{caminho no container} -d -p 8000:80 {nome da imagem}
```

* cria uma imagem chamada “custom-nginx” (pode ser o nome que você quiser) se baseando no que foi passado no arquivo dockerfile que está na mesma pasta (por isso o ponto).

```shell
  docker build -t custom-nginx .
```

* Para se logar com a conta do Docker Hub.

```shell
  docker login -u ramonmateus
```

* Envia a imagem selecionada para o seu repositório de imagens no Docker Hub.

```shell
  docker push {nome da imagem}
```

* Sobe os container especificados no arquivo “docker-compose.yaml” em modo background.

```shell
  docker compose up -d
```

* Lista os containers que estão rodando juntos pelo Docker-Compose.

```shell
  docker compose ps
```

* Executa o terminal bash no container (serviço especificado no arquivo “docker-compose.yaml”).

```shell
  docker compose exec {nome serviço} bash
```

* Roda o container com a imagem do mysql já passando a senha do root e o banco que você quer criar.

```shell
  docker run --env MYSQL_ROOT_PASSWORD=root --env MYSQL_DATABASE=meu_banco mysql:5.7
```

* Comando para quando tiver dentro do container entrar no cliente do mysql usando as configurações passadas no comando acima.

```shell
  mysql -uroot -proot
```
