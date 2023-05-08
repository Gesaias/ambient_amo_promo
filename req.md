# Descrição
O projeto foi divido em 3 etapas e 2 serviços, sendo um deles um WebService para atualizar diáriamente a base de dados de aeroportos em cache de consulta através de um Job que é executado todos os dias as 00:05 horas para fazer a atualização e também através de uma chamada de uma rota, consulta de viagens somente ida e ida-volta e fornecer os dados salvos e tratados pelo serviço além dos endpoints disponiveis, o segundo serviço contém um front-end com autenticação de um usuário padrão para alterar o status de cada aeroporto em que o cache contém, podendo adicionar descrição, vizualização dos aeroportos disponíveis e alteração de disponibilidade do aeroporto.

# Instruções
### Para iniciar o projeto em docker siga:

Na pasta raiz do projeto execute:

```
$ docker compose up -d
```

e o projeto vai se autoconfigurar e rodar as aplicações para começar a testar. Mas caso deseje rodar o projeto separadamente siga os proximos passos.

### Para rodar o projeto separadamente siga os passos:
#### Instale o nodejs na versão 18 stable ou superior
NodeJs: https://nodejs.org/en

#### Instale o flutter
Flutter: https://docs.flutter.dev/get-started/install

#### WebService Run
Instale os pacotes necessários em sua máquina e do projeto:
```
$ npm run i -g nestjs/cli ts-node && npm i
```

Rode as seeds necessárias e logo após suba o projeto:
```
$ npm run seed && npm run start:dev
```

Após isso o webservice terá a base de dados populada, um usuário padrão será criado para fazer o login e pegar o token necessário para acessar os endpoints pois são protegidos com auth token. Para fazer o login use o endpoint "http://localhost:3001/auth/login" passando o JSON {"username": "admin", password: "Abc@123456"} e o token retornado deve ser passado no header "Authorization: Bearer token" para acessar os outros endpoints. A documentação da API esta no endpoint "http://localhost:3001/api/document".

#### Api Painel Admin Run
Instale os pacotes necessários em sua máquina e do projeto:
```
$ npm run i -g nestjs/cli ts-node && npm i
```

Rode as seeds necessárias e logo após suba o projeto:
```
$ npm run seed && npm run start:dev
```

Após isso a aplicação back-end está pronta para consumir o webservice e para trabalhar com o front-end. Também foi criado um usuário padrão para acesso na API e seus endpoints, esse usuário serve também para login no Front-End. Para fazer o login acesse "http://localhost:3004/auth/login" com o JSON {"username": "admin", password: "Abc@123"} e será retornado um token para acessar os demais endpoints. A documentação da API está no endpoint "http://localhost:3004/api/document".

#### Painel Admin Run
Instale as dependecias necessárias do flutter:
```
$ flutter doctor && flutter run pub get
```

Agora rode o comando para subir a aplicação:
```
$ flutter run --profile -d web-server --web-port 3000 --web-hostname 0.0.0.0
```

Após isso a aplicação Front-End estará pronta para uso com o usuário "demo" e a senha "Abc@123" para conseguir fazer login e consumir os serviços(A aplicação front end depende da API Painel Admin para funcionar corretamente).

### Rotas do desafio
- Pesquisar viagens ida e volta: http://localhost:3001/trips/search/:going/:destiny/:departure_date/:back_date
- Pesquisar viagens ida: http://localhost:3001/trips/search/:going/:destiny/:departure_date
- Update cache de aeroportos: http://localhost:3001/airports/update/cache

## Resumo
Nestes projetos foram utilizados o framework Flutter para desenvolver a aplicação front-end web e o framework NestJs para fazer os serviços back-end. O framework Flutter é um framework multiplataforma onde é possível com uma base de só compilar a aplicação para Android, IOS, Windows, MacOS, Linux e Web, escolhi ele por ter mais afinidade apesar de também trabalhar com frameworks javascript e typescript, já o NestJS é um framework NodeJs usado para fazer aplicações back-end escalaveis e faceis de configurar, a documentação do framework é excelente para ajudar o desenvolvedor a usar o framework, també o escolhi por ter uma afinidade maior do que com outros frameworks ou linguagens.
