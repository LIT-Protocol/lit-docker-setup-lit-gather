# Docker setup for Lit-Gather

- Backend: `3000`
- Frontend: `3001`
- GatherController: `3002` ← In game event listener and communicate to the database
- oAuth: `4001`
- Database: `postgres://postgres@localhost:5432/lit_gateway_dev`

# Getting Started

## Download the required extensions

- [Remote - Containers | Publisher: Microsoft](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

## Setting up visual studio remote container with docker

- download the docker setup repo
- `./download.sh` run this bash script to download all required repositories:
```
https://github.com/LIT-Protocol/LitGatewayBackend.git
https://github.com/LIT-Protocol/LitGatewayFrontend.git
https://github.com/LIT-Protocol/GatherController.git
https://github.com/LIT-Protocol/lit-oauth.git
```
- Open `docker-compose.yml.example` and set all the required environment variables
- Rename `.example` at the end of the file name
- Ctrl + Shift + P to select `Remote-Containers: Open Folder in Container..`
- The docker will be running both nodejs backend and the database, but not the front-end and controller

## **Setting up Node.js Backend**

- `cd lit_backend` 
- `yarn` in the repo
- `yarn migrate` to run the migrate.js script
- `yarn knexMigrate` to run the SQL query for postgres
- `yarn global add nodemon` to install nodemon
- `PORT=3000 yarn startDev` to run

> You might run into issue that `yarn` is `unable to connect to github.com`. If that's the case you might have to re-write the default protocol of Github by running this code: `git config --global url.https://github.com/.insteadOf git://github.com/` (Note that there's no type, it is "insteadOf")

Now, these APIs will be available for the frontend

- `https://localhost:3000/oauth/gather/callback`
- `https://localhost:3000/user`

## Setting up the React Frontend

- `cd lit_frontend && yarn`
- `PORT=3001 yarn start` to run

## Setting up Lit-Gather Controller

- `cd lit_gather_controller && yarn`
- `PORT=3002 yarn startDev` to run

## Setting up oAuth

- `cd lit_oauth && yarn`
- `yarn global add concurrently`
- `yarn add fastify`
- `yarn add fastify-cors`
- `yarn add fastify-static`
- `yarn add fastify-objectionjs`
- `yarn add googleapis`
- `yarn startDev`