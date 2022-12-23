FROM node:16.13.2
WORKDIR /src/app
COPY . .
RUN npm install
RUN npm run build --prod
CMD ng serve --host 0.0.0.0 --port 4200