# Use a imagem do Node.js
FROM node:18-alpine

# Copie o código-fonte da API para o contêiner
COPY . /app

# Defina o diretório de trabalho
WORKDIR /app

# Instale as dependências da API
RUN npm install
# RUN npm run seed

# Compile a API
RUN npm run build

# Exponha a porta da API
EXPOSE 3004

# Defina o comando para iniciar a API
CMD ["npm", "run", "start:dev"]
