# Use the official Node.js image as a base image
FROM node:20.13.1

# Set the working directory
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Remove node_modules and package-lock.json to ensure a clean install
RUN rm -rf node_modules package-lock.json

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Expose the frontend port
EXPOSE 5173

# Start the application using the dev script
CMD ["npm", "run", "dev"]
