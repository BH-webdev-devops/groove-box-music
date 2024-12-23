# Use a Node.js base image
FROM node:16

# Define ARGs
ARG DATABASE_HOST
ARG DATABASE_PORT
ARG DATABASE_NAME
ARG DATABASE_USER
ARG DATABASE_PASSWORD
ARG DB_TYPE
ARG PORT
ARG JWT_SECRET
ARG GENIUS_HOST
ARG GENIUS_CLIENT_ID
ARG GENIUS_CLIENT_SECRET
ARG GENIUS_CLIENT_ACCESS_TOKEN
ARG DEFAULT_EXPIRATION_TIME
ARG RENDER_API_KEY
ARG REDIS_URL
ARG GCP_REGION

# Use ARGs in ENV
ENV DATABASE_HOST=${DATABASE_HOST}
ENV DATABASE_PORT=${DATABASE_PORT}
ENV DATABASE_NAME=${DATABASE_NAME}
ENV DATABASE_USER=${DATABASE_USER}
ENV DATABASE_PASSWORD=${DATABASE_PASSWORD}
ENV DB_TYPE=${DB_TYPE}
ENV PORT=${PORT}
ENV JWT_SECRET=${JWT_SECRET}
ENV GENIUS_HOST=${GENIUS_HOST}
ENV GENIUS_CLIENT_ID=${GENIUS_CLIENT_ID}
ENV GENIUS_CLIENT_SECRET=${GENIUS_CLIENT_SECRET}
ENV GENIUS_CLIENT_ACCESS_TOKEN=${GENIUS_CLIENT_ACCESS_TOKEN}
ENV DEFAULT_EXPIRATION_TIME=${DEFAULT_EXPIRATION_TIME}
ENV RENDER_API_KEY=${RENDER_API_KEY}
ENV REDIS_URL=${REDIS_URL}
ENV GCP_REGION=${GCP_REGION}


# Set the working directory
WORKDIR /

# Copy package files
COPY package*.json ./

# Install dependencies
RUN npm install

#  Install TypeScript globally
RUN npm install -g typescript

# Copy the source code
COPY . .

# Build TypeScript code
RUN npm run build

# Expose the port (if needed)
EXPOSE 8080

# Start the application
CMD ["node", "dist/server.js"]
