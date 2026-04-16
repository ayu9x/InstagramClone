# Construct a generic Firebase CLI wrapper for the cloud functions
FROM node:16-alpine
WORKDIR /app

# Emulators require Java runtime
RUN apk add --no-cache openjdk11-jre bash

RUN npm install -g firebase-tools

# Set up the internal functions dependencies
COPY functions/package*.json ./functions/
RUN cd functions && npm install

COPY . .

EXPOSE 4000 5001 8082

# Start the Emulator suite inside Docker
CMD ["firebase", "emulators:start", "--project", "demo-test"]
