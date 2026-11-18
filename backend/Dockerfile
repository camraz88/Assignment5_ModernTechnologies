# Use Node.js for base image
FROM node:18-alpine

# Puts a working directory inside the container
WORKDIR /app

# Copies package.json and package-lock.json
COPY package*.json ./

# Installs dependencies
RUN npm install

# Copies all app files
COPY . .

# Creates a directory for the SQLite database file
RUN mkdir -p /app/data

# Moves recipes.db into /app/data so the database is saved in the volume
RUN ln -sf /app/data/recipes.db /app/recipes.db

# Exposes the port the backend runs on
EXPOSE 5000

# Starts the app
CMD ["npm", "start"]