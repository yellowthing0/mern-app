# server/Dockerfile
FROM node:18-alpine

# Create app dir
WORKDIR /app

# Install deps first (better caching)
COPY package*.json ./
# If your "start" script uses nodemon, use `npm ci` (no --only=production)
RUN npm ci --only=production

# Copy source
COPY . .

# Environment (can be overridden at runtime)
ENV NODE_ENV=production \
    PORT=5000

# Docs-only; Compose publishes 5000:5000
EXPOSE 5000

# Start the server (expect "start": "node server.js" in package.json)
CMD ["npm", "start"]