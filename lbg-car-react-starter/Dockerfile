# Use an official Node.js 16 image
FROM node:16-alpine

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

# Define the command to start your application (adjust as needed)
CMD ["npm", "run", "start"]