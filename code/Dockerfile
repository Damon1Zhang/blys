FROM node:23.11.0-alpine3.21
ADD . /app
RUN cd /app && npm install

WORKDIR /app
EXPOSE 3099

ENTRYPOINT ["npm","run","start"]
