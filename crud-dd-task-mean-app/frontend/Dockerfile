# Stage 1: Build Angular
FROM node:18-alpine as build

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build --prod

# Stage 2: Serve with nginx
FROM nginx:alpine

# Create non-root user
RUN addgroup -S appgroup && adduser -S appuser -G appgroup

# Give permissions
RUN chown -R appuser:appgroup /usr/share/nginx/html

USER appuser

EXPOSE 8082

CMD ["nginx", "-g", "daemon off;"]