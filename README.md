# Description
The project was divided into 3 stages and 2 services, one of them being a WebService to daily update the database of airports in query cache through a Job that runs every day at 00:05 am to update and also through a route call, one-way and round-trip travel query and providing the data saved and processed by the service in addition to the available endpoints, the second service contains a front-end with authentication of a standard user to change the status of each airport in which the cache contains, being able to add description, visualization of available airports and change of airport availability.

# Instructions
### To start the project in docker follow:

In the root folder of the project run:

```
$ docker compose up -d
```

and the project will configure itself and run the applications to start testing. But if you want to run the project separately, follow the next steps.

### To run the project separately, follow these steps:
#### Install nodejs on version 18 stable or higher
NodeJs: https://nodejs.org/en

#### Install flutter
Flutter: https://docs.flutter.dev/get-started/install

#### WebService Run
Install the necessary packages on your machine and from the project:
```
$ npm run i -g nestjs/cli ts-node && npm i
```

Run the necessary seeds and then upload the project:
```
$ npm run seed && npm run start:dev
```

After that, the webservice will have the database populated, a standard user will be created to login and get the token needed to access the endpoints as they are protected with auth token. To login use the endpoint "http://localhost:3001/auth/login" passing the JSON {"username": "admin", password: "Abc@123456"} and the returned token must be passed in the "Authorization: Bearer token" header to access the other endpoints. The API documentation is in the "http://localhost:3001/api/document" endpoint.

#### Dashboard Admin Run API
Install the necessary packages on your machine and from the project:
```
$ npm run i -g nestjs/cli ts-node && npm i
```

Run the necessary seeds and then upload the project:
```
$ npm run seed && npm run start:dev
```

After that, the back-end application is ready to consume the webservice and to work with the front-end. A standard user was also created to access the API and its endpoints, this user is also used to login to the Front-End. To login, access "http://localhost:3004/auth/login" with the JSON {"username": "admin", password: "Abc@123"} and a token will be returned to access the other endpoints. The API documentation is in the "http://localhost:3004/api/document" endpoint.

#### Admin Run Dashboard
Install the necessary flutter dependencies:
```
$ flutter doctor && flutter run pub get
```

Now run the command to load the application:
```
$ flutter run --profile -d web-server --web-port 3000 --web-hostname 0.0.0.0
```

After that, the Front-End application will be ready for use with the user "demo" and the password "Abc@123" to be able to login and consume the services (The front-end application depends on the Admin Panel API to work correctly).

### Challenge routes
- Search round trips: http://localhost:3001/trips/search/:going/:destiny/:departure_date/:back_date
- Search one way trips: http://localhost:3001/trips/search/:going/:destiny/:departure_date
- Update airport cache: http://localhost:3001/airports/update/cache

## Summary
In these projects, the Flutter framework was used to develop the front-end web application and the NestJs framework to make the back-end services. The Flutter framework is a cross-platform framework where it is possible with a base of only compiling the application for Android, IOS, Windows, MacOS, Linux and Web, I chose it because it has more affinity despite also working with javascript and typescript frameworks, as for NestJS It is a NodeJs framework used to make scalable and easy to configure back-end applications, the framework documentation is excellent to help the developer to use the framework, I also chose it because it has a greater affinity than with other frameworks or languages.

#### Below are links to each project developed separately:
WebService API: https://github.com/Gesaias/daily_consumption_api
Dashboard Admin APP: https://github.com/Gesaias/administrative_panel_app
Admin API: https://github.com/Gesaias/administrative_panel_api
