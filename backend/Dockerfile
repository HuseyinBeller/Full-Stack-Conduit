# Use the official NodeJS image as a base image
FROM node:20


# Set the Working directoy inside the container
WORKDIR /usr/src/app

# Copy the package.json and package-lock.json to working directory
COPY package*.json ./


# Install dependencies
RUN npm install && npm run install mysql2 


# Copy the backend source code to the working directory
COPY . .


# Copy the .env file to the container
COPY .env .env

RUN npm run sqlz db:create && npm run sqlz db:migrate && npm run sqlz db:seed


# Expose the backend port
EXPOSE 3001


# Command to run the backend server
CMD ["npm", "run", "dev"]


