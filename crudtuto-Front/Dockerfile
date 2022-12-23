FROM node:16.13.2
RUN mkdir -p /home/server
WORKDIR /home/serveur
COPY . /home/serveur
RUN npm install
EXPOSE 4200
CMD ["ng", "serve"]