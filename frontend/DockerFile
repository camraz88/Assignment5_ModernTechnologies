# STAGE 1
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

# Backend URL for the browser and Vite puts the value into the app
ARG VITE_API_URL=http://localhost:5000
ENV VITE_API_URL=$VITE_API_URL

# Builds the production app
RUN npm run build

# STAGE 2
# Uses nginx for the final build
FROM nginx:alpine
COPY --from=0 /app/dist /usr/share/nginx/html

# Expose port 80, which is nginx default
EXPOSE 80

# Runs nginx in the foreground so the container keeps running
CMD ["nginx", "-g", "daemon off;"]