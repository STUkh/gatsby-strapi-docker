FROM node:11-alpine

# Also exposing VSCode debug ports
EXPOSE 8000 9929 9230

# Create and set workdir
RUN mkdir -p /home/gatsby-app
WORKDIR /home/gatsby-app

# Install linux system dependencies for alpine
RUN \
  apk add --no-cache python make curl g++ && \
  apk add vips-dev fftw-dev --no-cache --repository http://dl-3.alpinelinux.org/alpine/edge/testing --repository http://dl-3.alpinelinux.org/alpine/edge/main && \
  rm -fR /var/cache/apk/*

# Install nodejs global packages
RUN npm install -g gatsby-cli

# Copy package.json to cache packages image layer
COPY package*.json ./

# Install nodejs local packages
RUN ["npm", "install"]

# Copy sourcecode files
COPY . .

RUN chmod +x ./wait-for-strapi.sh

# Node image provide build-in non-root user
#USER node

#CMD ["gatsby", "develop", "-H", "0.0.0.0" ]
