# Stage 1: Build React application
FROM node:18-alpine AS build

# Set working directory
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install frontend dependencies
RUN npm install
# Accept build argument
ARG VITE_API_URL
ENV VITE_API_URL=$VITE_API_URL

# Copy all frontend files
COPY . .

# Build production-ready React app
RUN npm run build

# Stage 2: Serve with Nginx
FROM nginx:alpine

# Copy built React files from previous stage to Nginx's html directory
COPY --from=build /app/dist /usr/share/nginx/html

# Expose port 80 (default for Nginx)
EXPOSE 80

# Start Nginx in the foreground
CMD ["nginx", "-g", "daemon off;"]
