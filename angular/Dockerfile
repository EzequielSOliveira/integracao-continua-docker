# Stage 1
FROM node:lts as node

WORKDIR /usr/src/app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build

# Stage 2
FROM nginx:latest

COPY --from=node /usr/src/app/dist/sgcmapp /usr/share/nginx/html

COPY ./nginx.conf /etc/nginx/conf.d/default.conf
