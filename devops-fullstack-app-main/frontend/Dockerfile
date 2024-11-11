# Use a Node.js base image for the build stage
FROM node:16 as build

# Set the working directory for the build
WORKDIR /app

# Copy only package.json and package-lock.json for npm install
COPY package*.json ./
RUN npm install

# Copy the rest of the application code
COPY . ./

# Build the React app for production
RUN npm run build --production

# Use Nginx as the base image for serving the app
FROM nginx:alpine

# Copy custom Nginx configuration (optional)
# COPY nginx.conf /etc/nginx/nginx.conf

# Copy the built app from the build stage into the Nginx HTML directory
COPY --from=build /app/build /usr/share/nginx/html

# Expose port 80 for HTTP traffic
EXPOSE 80

# Start the Nginx server
CMD ["nginx", "-g", "daemon off;"]
