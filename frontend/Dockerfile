# Use Node 12 as base image since that's the minimum specified in your engines

FROM node:12-alpine

# Create app directory
WORKDIR /app

# Copy package files
COPY package*.json ./

# Install dependencies and build tools
RUN apk add --no-cache python2 make g++ && \
    npm install --no-save \
    webpack@latest \
    webpack-dev-middleware@latest \
    webpack-hot-middleware@latest \
    webpack-bundle-analyzer@latest \
    webpack-merge@latest && \
    npm install

# Copy project files
COPY . .

# Build the app
RUN npm run build

# Expose the port (assuming default Vue development port)
EXPOSE 3000

# Start the application
CMD ["npm", "run", "start"]