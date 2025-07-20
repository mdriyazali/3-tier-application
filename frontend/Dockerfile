# Use an official Node.js runtime as the base image
FROM node:14-alpine

# Set working directory
WORKDIR /app

# Install dependencies separately to leverage Docker cache
COPY package.json package-lock.json ./
RUN npm install --frozen-lockfile

# Copy app files
COPY . .

# Expose the port the app runs on
EXPOSE 3000

# Start the application
CMD ["npm", "start"]
