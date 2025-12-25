# Stage 1: Build the React app
FROM node:18 AS build

WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy all other frontend files
COPY . .

# Build the React app for production
RUN npm run build

# Stage 2: Serve the app using nginx
FROM nginx:alpine

# Copy the built app from previous stage
COPY --from=build /app/build /usr/share/nginx/html

# Expose port 80
EXPOSE 80

# Start nginx
CMD ["nginx", "-g", "daemon off;"]
