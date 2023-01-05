FROM node:16.13.2

# Create a directory where our app will be placed
RUN mkdir -p /app

# Change directory so that our commands run inside this new directory
WORKDIR /app

# Copy dependency definitions
COPY package*.json ./

RUN ls -al
# Install dependecies
RUN npm install

# Get all the code needed to run the app
COPY . ./

# Expose the port the app runs in
EXPOSE 4200

# Serve the app
CMD ["npm", "start"]