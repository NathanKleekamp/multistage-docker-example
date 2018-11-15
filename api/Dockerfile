FROM node:8.12-alpine

COPY ./app /app

WORKDIR /app

RUN npm ci

EXPOSE 80

CMD ["npm", "start"]
