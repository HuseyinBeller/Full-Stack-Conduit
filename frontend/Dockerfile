# Use the official Node.js image as a base image
FROM node:20

# Set the working directory inside the container
WORKDIR /usr/src/app

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the frontend source code to the working directory
COPY . .

# Build the frontend application
RUN npm run build

# Use a lightweight web server to serve the static files
FROM nginx:alpine
COPY --from=0 /usr/src/app/dist/assets /usr/share/nginx/html

# Expose the frontend port
EXPOSE 3000

# Command to run the web server
CMD ["nginx", "-g", "daemon off;"]
