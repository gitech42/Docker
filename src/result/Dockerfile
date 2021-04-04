FROM node:12-alpine

RUN apk add --update nodejs-current npm

USER node

RUN mkdir /home/node/code

WORKDIR /home/node/code

COPY package.json package.json

RUN npm install

COPY . .

EXPOSE 80

CMD [ "node", "server.js" ]