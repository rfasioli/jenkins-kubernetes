# Jenkins em larga escala com kubernetes
Repositório do curso Jenkins em larga escala com kubernetes.
**Wiki:** https://gitlab.com/rocha.public/cursos/jenkins-em-larga-escala/-/wikis/home

## v0.1.0
### Build e Push
```
docker build . --tag <usuario-docker-hub>/missao-devops-jenkins:<versao>
docker login
docker push <usuario-docker-hub>/missao-devops-jenkins:<versao>
```
### Run
```
docker run --name docker-jenkins -p 8080:8080 <usuario-docker-hub>/missao-devops-jenkins:<versao>
```
### Comandos docker
```
docker images
docker start <nome-container>
docker logs <container>
```

## v0.2.0
Na versão 0.2.0 são instalados os plugins. Para gerar a imagem e executar, utilizar os mesmos comandos da versão 0.1.0.
No curso:
 - Configuramos senha
 - Configuramos Jdk

## v0.3.0
Na versão 0.3.0 é feita a automação de backups. No docker file são configuradas algumas pastas.
Para gerar a imagem, utilizar os mesmos comandos da versão 0.2.0.
Para execução, vamos expor as pastas de backup e execução através de volumes para a máquina local.
### Run
```
docker run --name docker-jenkins-3 \
    -p 8080:8080 \
    -v jenkins_home_3:/var/jenkins_home \
    -v jenkins_backup_3:/srv/backup \
    <usuario-docker-hub>/missao-devops-jenkins:0.3.0
```
### Atividades
- Login na Ferramenta
- Troca de Senha
- Configuração da JDK
- Criação de 2 Jobs
- Configurar Backup
- Executar Backup
- Obter Backup
O backup será feito para a pasta local `/var/jenkins_home`

## v0.4.0
Na versão 4 iremos restaurar as configurações do backup no build da imagem
### Build e Push
```
docker build . --tag <usuario-docker-hub>/missao-devops-jenkins:0.4.0
```
### Run
```
docker run --name docker-jenkins-4 \
    -d \
    -p 8080:8080 \
    -v jenkins_home_4:/var/jenkins_home \
    -v jenkins_backup_4:/srv/backup \
    <usuario-docker-hub>/missao-devops-jenkins:0.4.0
```

## v1.0.0
Na versão 1 foram atualizados os plugins no curso. para gerar a imagem e executar o container podem ser utilizados os mesmos comandos da versão 0.4.0

## v.1.1.0
Nesta versão a 1.1.0, foi atualizada a versão do jenkins e plugins para a data atual.
### Build
```
docker build . --tag <usuario-docker-hub>/missao-devops-jenkins:1.1.0
```
### Run
```
docker run --name docker-jenkins-110 \
    -d \
    -p 8080:8080 \
    -v jenkins_home_110:/var/jenkins_home \
    -v jenkins_backup_110:/srv/backup \
    <usuario-docker-hub>/missao-devops-jenkins:1.1.0
```
