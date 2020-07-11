# Pull base image.
FROM node:12

# Create app directory
WORKDIR /usr/src/app

# Install app dependencies
COPY package*.json ./

# global install gulp and jshint
RUN npm install && npm install -g gulp jshint

# Bundle app source
COPY . .

EXPOSE 3000

CMD ["make", "serve"]