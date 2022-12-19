FROM node:19

## Building the application
# create a directory /app and cd into in
WORKDIR /app

ADD main.js .
ADD package.json .
ADD package-lock.json .
ADD views views
ADD public public

# Install the node_modules
RUN npm ci

## Run the application
# Set the APP_PORT to 3000
ENV APP_PORT=3000 

# Health check
HEALTHCHECK --interval=30s --timeout=5s --start-period=5s --retries=3 \
    CMD curl -s http://localhost:${APP_PORT}/health || exit 1

# What part does the application bind to
EXPOSE ${APP_PORT}

# Start the application
ENTRYPOINT node main.js