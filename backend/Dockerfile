# Use official Node.js 18 image as base
FROM node:18

# Set working directory inside container
WORKDIR /app

# Copy package files first (for caching)
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy all backend source code
COPY . .

# Expose the backend port
EXPOSE 2000

# Start the backend server
CMD ["node", "server.js"]
