# Stage 1: Build the React application using Node.js 16 to avoid OpenSSL issues
FROM node:16-alpine AS build

# Set working directory
WORKDIR /app

# Copy package files and install dependencies
COPY package.json ./
COPY package-lock.json ./
RUN npm install

# Copy the rest of the application
COPY . .

# Build the React app for production
RUN npm run build

# Stage 2: Serve the static files with Nginx
FROM nginx:1.25.2-alpine

# Copy the built static files from the build stage
COPY --from=build /app/build /usr/share/nginx/html

# Copy custom Nginx configuration if available
COPY nginx/nginx.conf /etc/nginx/conf.d/default.conf

# Expose port 80
EXPOSE 80

# Start Nginx in the foreground
CMD ["nginx", "-g", "daemon off;"]
