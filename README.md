# Docker
Docker Scripts and Studies


## Criando um imagem simples para trabalhar com container docker um ambiente NODEJS em Windows 

FROM node:latest
### Informando o autor
LABEL maintainer="Alessandro S Borges" 
### Variaveis de Ambiente
ENV NODE_ENV=developer
ENV PORT=3000
### Informando que será copiado tudo da pasta de origem para o caminho no container
COPY . /var/www/node/Service_Node
### Informa qual será o Work Director (Diretório de Trabalho)
WORKDIR /var/www/node/Service_Node 
### Intalando a pasta node_modules
RUN npm install
### Entrypoint é o comado executado logo depois do Start do Node pode ser colocado dento de um array JSON
ENTRYPOINT npm start
### Informa que ira usa a porta 3000 no conatiner que obteve s informação de ENV PORT=3000
EXPOSE $PORT

#### Comando para executar no terminal: docker build -f node.Dockerfile -t alessandroasb/node .
docker build é o comando
#### -f para informar o nome do arquivo, se for padrão Dockerfile apenas não precisa
#### -t para inserir uma tag na imagem, geralmente nome de que criou
##### Depois de executar terá sido criado uma imagem
##### para usar a imagem como um container, executar o comando abaixo:
docker run -p 8080:3000 -v "e:\Docker_Repo\node\Service_Node:/var/www/node/Service_Node" -w "/var/www/node/Service_Node"  --name Node_pluginbot node npm start
