# Use a imagem do Flutter SDK
FROM ghcr.io/cirruslabs/flutter:stable

# Copie o código-fonte da aplicação para o contêiner
COPY . /app

# Defina o diretório de trabalho
WORKDIR /app

# Instale as dependências da aplicação
RUN flutter pub get

EXPOSE 3000

# Compile a aplicação
RUN flutter build web --profile

CMD ["flutter", "run", "--profile", "-d", "web-server", "--web-port", "3000"]
