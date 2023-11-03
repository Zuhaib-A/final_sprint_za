# Stage 1: Build the React app
FROM node:16-alpine as build

# Change into a folder called /app
WORKDIR /app

# Only copy package.json
COPY package.json .

# Download the project dependencies
RUN npm install

# Copy everything from the React app folder to the /app folder in the container
COPY . .

# Set the SERVER_URL using an ARG (default value is "localhost")
ARG SERVER_URL=localhost

# Copy the script to set the environment variable
COPY 

# Make the script executable and execute it
RUN chmod +x set_env.sh
RUN ./set_env.sh

# Package up the React project in the /app directory
RUN npm run build

# Stage 2: Serve the React app using Nginx
FROM nginx:1.23-alpine

# Copy the built React app from the previous stage to the Nginx web root
COPY --from=build /app/build /usr/share/nginx/html

# Copy your custom Nginx configuration
COPY nginx/nginx.conf /etc/nginx/conf.d/default.conf

# Expose port 80
EXPOSE 80

# Start the Nginx server
CMD ["nginx", "-g", "daemon off;"]