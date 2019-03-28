# Node.js and Express To-Do API Secured with Auth0

To learn how to develop APIs similar to this one, check this article: https://auth0.com/blog/node-js-and-express-tutorial-building-and-securing-restful-apis/

## Running

To run this sample, you can either use Docker to decouple the server from the host machine, or you can use Node.js and NPM. Fell free to choose whatever suits you better.

### Running with NPM and Node.js

First, you will need to clone this repo in the host machine. After that, on a terminal, run the following commands:

```bash
# move into the project root
cd to-do-apis

# install its dependencies
npm install

# define your own env variables
export AUTH0_DOMAIN=...
export AUTH0_API=...
export AUTH0_CLIENT_ID=...
export AUTH0_CLIENT_SECRET=...

# run the application
npm start
```

### Running with Docker

There is [an image on Docker Hub](https://cloud.docker.com/u/auth0blog/repository/docker/auth0blog/to-dos-api-express) that you can use. To run it, issue the following command:

```bash
AUTH0_DOMAIN=...
AUTH0_API=...
AUTH0_CLIENT_ID=...
AUTH0_CLIENT_SECRET=...

docker run \
  -p 3001:3001 \
  -e "AUTH0_DOMAIN="$AUTH0_DOMAIN \
  -e "AUTH0_API="$AUTH0_API \
  -e "AUTH0_CLIENT_ID="$AUTH0_CLIENT_ID \
  -e "AUTH0_CLIENT_SECRET="$AUTH0_CLIENT_SECRET \
  --name to-dos \
  -d auth0blog/to-dos-api-express:auth0
```

This will run the project on a Docker container and expose the API on port `3001` on the host. Feel free to adjust these setting to your needs.

## Consuming the API

This is a HTTP API (or a RESTful API, if you will). As such, to consume this API you will need to issue HTTP requests from some client. For example, you can use Postman, Insomnia, `curl`, etc. The following commands show how use the latter:

```bash
# request all to-do items
curl localhost:3001

# insert a new to-do
curl -X POST -H 'Content-Type: application/json' -d '{
  "message": "Buy some yummy pizza!"
}' http://localhost:3001/
```
