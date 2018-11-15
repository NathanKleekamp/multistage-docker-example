# Base

FROM node:8.12-alpine AS base

COPY ./app/package.json ./app/package-lock.json /app/

WORKDIR /app

RUN npm ci

# Development

FROM base AS development

CMD ["npm", "run", "serve"]

EXPOSE 8080

# Production builder

FROM base AS productionBuilder

RUN npm run build

# Production

FROM nginx:1.15-alpine as production

WORKDIR /root/

COPY --from=productionBuilder /app/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]

