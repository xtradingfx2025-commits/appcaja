FROM node:20-alpine

WORKDIR /app

# Copy package files
COPY package*.json ./
COPY ./src/* /app/

# Install dependencies
RUN npm install

# Set environment variables
ENV NODE_ENV=development
ENV AMQP_URL=amqp://rabbitmq

# Command to run the application with nodemon for hot-reloading
CMD ["npm", "run", "dev"]
