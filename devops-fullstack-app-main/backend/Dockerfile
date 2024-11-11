# Build Stage
FROM node:14.17.0 as build

# Set the working directory for the build stage
WORKDIR /usr/src/app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies using npm ci for a cleaner install
RUN npm ci

# Copy the rest of the application code
COPY . .

# Production Stage (smaller image)
FROM node:14.17.0

# Set the working directory for the runtime container
WORKDIR /usr/src/app

# Copy only the necessary files from the build stage
COPY --from=build /usr/src/app /usr/src/app

# Expose the port for the backend
EXPOSE 3000

# Start the backend server
CMD ["node", "server.js"]
