FROM node:14.17.0

# Set the working directory
WORKDIR /usr/src/app

# Copy package.json and install dependencies
COPY package*.json ./
RUN npm install

# Copy the rest of the app source code
COPY . .

# Expose the port your app will run on
EXPOSE 3000

# Start the backend server
CMD ["node", "server.js"]
