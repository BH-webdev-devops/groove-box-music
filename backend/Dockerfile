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

# Use ARGs in ENV
ENV DATABASE_HOST=${DATABASE_HOST}
ENV DATABASE_PORT=${DATABASE_PORT}
ENV DATABASE_NAME=${DATABASE_NAME}
ENV DATABASE_USER=${DATABASE_USER}
ENV DATABASE_PASSWORD=${DATABASE_PASSWORD}
ENV DB_TYPE=${DB_TYPE}
ENV PORT=${PORT}
ENV JWT_SECRET=${JWT_SECRET}

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
EXPOSE ${PORT}

# Start the application
CMD ["node", "dist/server.js"]
