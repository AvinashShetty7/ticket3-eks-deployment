FROM node:26-alpine3.23 AS builds

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . ./

RUN npm run build



FROM nginx:1.31.3

COPY --from=builds ./app/dist/  /usr/share/nginx/html/

CMD ["nginx", "-g", "daemon off;"]