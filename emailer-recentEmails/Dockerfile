# Build Container
FROM node:15.8.0-stretch

WORKDIR /build

COPY package-lock.json package.json ./

RUN npm ci

COPY . .

# Runtime container
FROM node:15.8.0-alpine3.10

USER node

RUN mkdir /home/node/emailer

WORKDIR /home/node/emailer

COPY --from=0 --chown=node:node /build .

CMD ["node", "server.js"]
