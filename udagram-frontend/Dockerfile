# Use ionic base image
FROM beevelop/ionic:latest AS ionic

# Create app working directory
WORKDIR /usr/src/app

# Install app dependencies by copying
# package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm ci

# Bundle app source
COPY . .

# Build ionic app
RUN ionic build

# Use nginx base image
FROM nginx:alpine

#COPY www /usr/share/nginx/html
COPY --from=ionic  /usr/src/app/www /usr/share/nginx/html