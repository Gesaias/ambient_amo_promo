FROM debian:stable-slim AS build-env

RUN apt-get update && apt-get install -y curl gnupg2 ca-certificates lsb-release
RUN curl -fsSL https://deb.nodesource.com/setup_18.x | bash -
RUN apt-get update && apt-get install -y git unzip nodejs

RUN git clone https://github.com/flutter/flutter.git /usr/local/flutter
ENV PATH "$PATH:/usr/local/flutter/bin"

RUN flutter channel stable && flutter upgrade && flutter config --enable-web

COPY . /app

WORKDIR /app

RUN flutter pub get
RUN flutter build web --release

FROM nginx:1.24.0-alpine-slim

COPY nginx.conf /etc/nginx/nginx.conf
COPY --from=build-env /app/build/web /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
