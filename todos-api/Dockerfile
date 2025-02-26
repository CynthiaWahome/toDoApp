# Use a more specific base image version for better stability
FROM node:14-slim

# Set working directory
WORKDIR /app

# Copy package files first to leverage Docker layer caching
COPY package*.json ./

# Install dependencies
RUN npm ci install

# Copy source code
COPY . .

# Expose port
EXPOSE 8082

# Start the application
CMD ["npm", "start"]