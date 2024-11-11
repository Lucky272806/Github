# Use a Node.js base image
FROM node:16 as build

# Set the working directory
WORKDIR /app

# Copy package.json and install dependencies
COPY package*.json ./
RUN npm install

# Copy the rest of the app source code
COPY . .

# Build the React app
RUN npm run build

# Use an Nginx base image to serve the built app
FROM nginx:alpine

# Copy build folder to Nginx's html folder
COPY --from=build /app/build /usr/share/nginx/html

# Expose port 80 for HTTP
EXPOSE 80

# Start Nginx server
CMD ["nginx", "-g", "daemon off;"]
