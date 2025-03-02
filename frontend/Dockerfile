# Use a stable Node.js version
FROM node:12-alpine

# Set working directory
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install build tools with Python 2 (required for node-sass)
RUN apk add --no-cache python2 make g++ && ln -sf /usr/bin/python2 /usr/bin/python

# Set Python environment variable for node-gyp
ENV PYTHON=/usr/bin/python2

# Clear npm cache and install dependencies
RUN npm cache clean --force && npm install --no-optional

# Copy the rest of the application code
COPY . .

# Build the frontend
RUN npm run build

# Expose the frontend port
EXPOSE 8080

# Start the frontend application
CMD ["npm", "start"]
