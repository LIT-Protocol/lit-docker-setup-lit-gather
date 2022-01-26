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

- `git clone repo` download the docker setup repo
- `./download.sh` run this bash script to download all required repositories
- Open `docker-compose.yml` and set all the required environment variables

## **Setting up Node.js Backend**

- `git clone https://github.com/LIT-Protocol/LitGatewayBackend.git`
- `yarn` in the repo
- `yarn migrate` to run the migrate.js script
- `yarn knexMigrate` to run the SQL query for postgres
- `yarn global add nodemon` to install nodemon
- `PORT=3000 yarn startDev` to run

Now, these APIs will be available for the frontend

- `https://localhost:3000/oauth/gather/callback`
- `https://localhost:3000/user`

## Setting up the React Frontend

- `git clone [https://github.com/LIT-Protocol/LitGatewayFrontend.git](https://github.com/LIT-Protocol/LitGatewayFrontend.git) lit_frontend`
- `cd lit_frontend && yarn`
- `PORT=3001 yarn start` to run

## Setting up Lit-Gather Controller

- `git clone [https://github.com/LIT-Protocol/GatherController.git](https://github.com/LIT-Protocol/GatherController.git) lit_gather_controller`
- `cd lit_gather_controller && yarn`
- `PORT=3002 yarn startDev` to run

## Setting up oAuth

- `git clone [https://github.com/LIT-Protocol/lit-oauth.git](https://github.com/LIT-Protocol/lit-oauth.git) lit_oauth`
- `cd lit_oauth && yarn`
- `yarn global add concurrently`
- `yarn add fastify`
- `yarn add fastify-cors`
- `yarn add fastify-static`
- `yarn add fastify-objectionjs`
- `yarn add googleapis`
- `yarn startDev`