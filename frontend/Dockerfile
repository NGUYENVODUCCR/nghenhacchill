# Build stage
FROM node:18-alpine as build

WORKDIR /app
COPY package.json ./
RUN npm install
COPY . .
RUN npm run build

# Production stage
FROM nginx:alpine

# Copy bản build sang nginx
COPY --from=build /app/build /usr/share/nginx/html

# Copy file cấu hình nginx nếu có
# COPY nginx.conf /etc/nginx/nginx.conf

# Expose cổng 80 cho Render
EXPOSE 3000

CMD ["nginx", "-g", "daemon off;"]
