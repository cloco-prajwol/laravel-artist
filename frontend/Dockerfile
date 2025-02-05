# # ---- Base Stage: Build ----
#     FROM node:18-alpine as build-stage

#     # Set working directory
#     WORKDIR /app
    
#     # Copy only package.json and package-lock.json first to leverage Docker cache
#     COPY package*.json ./
    
#     # Install dependencies without saving cache
#     RUN npm install --frozen-lockfile --omit=dev
    
#     # Copy source code
#     COPY . .
    
#     # Build project
#     RUN npm run build
    
#     # ---- Production Stage ----
#     FROM nginx:alpine as production-stage
    
#     # Remove default Nginx static files
#     RUN rm -rf /usr/share/nginx/html/*
    
#     # Copy only built files from the previous stage
#     COPY --from=build-stage /app/dist /usr/share/nginx/html
    
#     # Expose port 80 for Nginx
#     EXPOSE 80
    
#     # Start Nginx in the foreground
#     CMD ["nginx", "-g", "daemon off;"]
    
    # ---- Production Stage ----
FROM nginx:alpine as production-stage

# Set working directory
WORKDIR /usr/share/nginx/html

# Copy built files from local machine to the container
COPY ./dist . 

# Expose port 80 for Nginx
EXPOSE 80

# Start Nginx in the foreground
CMD ["nginx", "-g", "daemon off;"]
