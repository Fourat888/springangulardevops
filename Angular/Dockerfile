FROM node:18.12.0 as node
WORKDIR /app
COPY . .
RUN npm install
RUN npm run build --prod

FROM nginx:alpine
COPY --from=node /app/dist/crudtuto-Front /usr/share/nginx/html