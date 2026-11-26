
# Stage 1: Build Quasar SPA
FROM node:22-alpine AS builder

WORKDIR /app

# Copy all source code and configuration first
COPY . .

# Install dependencies
RUN npm ci --legacy-peer-deps

# Build Quasar
RUN npm run build

# Stage 2: Production with Nginx
FROM nginx:1.27-alpine

# Copy build artifacts
COPY --from=builder /app/dist/spa /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
