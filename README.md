## Description

This project will create a fully working JWT authenticated server using Nest.js and implements JWT (JSON Web Tokens) Authentication. It will use access tokens to get new refresh tokens. It will use the [Nest](https://github.com/nestjs/nest) framework as our server and have two resources, user and auth. It can be tested using Postman to make sure the correct replies are received. 

## Running the app

```bash
# development
$ npm run start

# watch mode
$ npm run start:dev

# production mode
$ npm run start:prod
```

## Packages
The following packages are required:
* class-validator
* jsonwebtoken
* @types/jsonwebtoken
* @nestjs/config
* passport
* @nestjs/passport
* passport-jwt
* @types/passport-jwt

## Other Requirements
To create my access and refresh secret keys I used [RandomKeygen](https://randomkeygen.com/)

## Testing
I used Postman to test the endpoints after the server is running on the local host.

To test the login, send a POST request to 'http://localhost:3000/auth/login' with the following JSON data in the body:
```
{
    "email": "bob@gmail.com",
    "password": "bobPass"
}
```
A new refresh token and access token will be returned. 

To test whether or not the user data is returned send a GET request to 'http://localhost:3000/users/me' with the access token retrieved in the previous step pasted into the Authorisation Bearer Token.

The user data will then be returned. 

To test the refresh so that a new refresh token is returned, send a POST request to 'http://localhost:3000/auth/refresh' with the refresh token retrieved in the first step sent as JSON data in the body:
```
{
    "refreshToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MCwiaXBBZGRyZXNzIjoiOjoxIiwidXNlckFnZW50IjoiUG9zdG1hblJ1bnRpbWUvNy4yOS4wIiwidXNlcklkIjowLCJpYXQiOjE2NDkxNTAxNDh9.GLx_TiDh0egukuc477oRnjYO12COAEfUXhbRZaEUNsI"
}
```
To test the delete so that the user is 'logged off' send a DELETE request to 'http://localhost:3000/auth/logout' with the refresh token retrieved in the first step sent as JSON data in the body:
```
{
    "refreshToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MCwiaXBBZGRyZXNzIjoiOjoxIiwidXNlckFnZW50IjoiUG9zdG1hblJ1bnRpbWUvNy4yOS4wIiwidXNlcklkIjowLCJpYXQiOjE2NDkxNTAxNDh9.GLx_TiDh0egukuc477oRnjYO12COAEfUXhbRZaEUNsI"
}
```
and the user will be logged out. 
