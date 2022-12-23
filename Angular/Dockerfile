FROM node:16.13.2
WORKDIR /app
COPY . .
RUN npm install
RUN npm run build --prod

FROM nginx:alpine
COPY --from=node /app/dist/Angular /usr/share/nginx/html