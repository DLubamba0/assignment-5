# Use Node.js 18 Alpine as the base image
FROM node:18-alpine

# Set working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install backend dependencies
RUN npm install

# Copy all backend application files
COPY . .

# Create a directory for the SQLite database
RUN mkdir -p /app/data

# Expose port 5000 (backend port)
EXPOSE 5000

# Start the backend application
CMD ["npm", "start"]
