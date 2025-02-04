# ---- Build Stage ----
    FROM node:18-alpine as build-stage

    # Set working directory
    WORKDIR /app
    
    # Copy package.json & install dependencies
    COPY package*.json ./
    RUN npm install --frozen-lockfile
    
    # Copy source code & build
    COPY . .
    RUN npm run build
    
    # ---- Production Stage ----
    FROM nginx:alpine as production-stage


    # Copy built files from build stage
    COPY --from=build-stage /app/dist /usr/share/nginx/html
    
    # Expose port 80 for Nginx
    EXPOSE 80
    
    # Start Nginx in the foreground
    CMD ["nginx", "-g", "daemon off;"]
    