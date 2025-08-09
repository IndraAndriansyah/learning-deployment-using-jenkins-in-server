# Stage 1: Build the Next.js app
FROM node:18-alpine AS builder

WORKDIR /app

# Install dependencies
COPY package*.json ./
RUN npm install

# Copy source files
COPY . .

# Build the Next.js app
RUN npm run build

# Stage 2: Run the production build
FROM node:18-alpine

WORKDIR /app

# Install only production dependencies
COPY package*.json ./
RUN npm install --production

# Copy built app from builder stage
COPY --from=builder /app ./

# Expose the default Next.js port
EXPOSE 3000

# Start the application
CMD ["npm", "start"]
