# Build from node:6.9.4 Images
FROM node:6.9.4

# Changing working directory
WORKDIR ./src

# Copy source to docker container
ADD ./src ./

# Install node packages
RUN npm install

# Start app using node cli
CMD ["node", "./app.js"]