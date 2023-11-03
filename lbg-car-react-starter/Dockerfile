# Use an official Node.js 16 image for building React app
FROM node:16-alpine as builder

# Change into a directory called /app
WORKDIR /app

# Only copy package.json
COPY package.json .

# Download project dependencies
RUN npm install

# Copy everything from the React app folder to the /app folder in the container
COPY . .

# Package up the React project in the /app directory
RUN npm run build

# Use an official Nginx image
FROM nginx:latest

# Remove the default Nginx configuration file
RUN rm /etc/nginx/conf.d/default.conf

# Copy your custom Nginx configuration file to the container
COPY nginx.conf /etc/nginx/conf.d/

# Copy the built React app to the Nginx web root
COPY --from=builder /app/build /usr/share/nginx/html

# Expose port 80
EXPOSE 80

# Start the Nginx server
CMD ["nginx", "-g", "daemon off;"]