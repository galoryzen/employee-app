FROM docker.io/node:16 as base
# Create app directory
WORKDIR /usr/src/app
# Copy and install app dependencies.
# When the environment is development the local dependencies are used since all
# the app should be mounted as a volume at /usr/src/app
COPY package*.json ./
RUN npm install
EXPOSE 8080
CMD [ "node", "server.js" ]

# In producion the source is not mounted, rather copied and the node_modules
# are fetched.
FROM base as production
COPY . .
RUN rm -rf node_modules
RUN npm install
