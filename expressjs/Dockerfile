# Build from node:6.9.4 Images
FROM node:6.9.4

WORKDIR ./src

# Copy source to docker container
ADD ./src ./
RUN npm install

# Start api using node cli
CMD ["node", "./app.js"]