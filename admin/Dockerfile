# Stage 1: Build the React Application
FROM node:14-alpine as build
WORKDIR /app
COPY package*.json ./
# Install dependencies, bypassing legacy-peer-deps errors
RUN npm install --legacy-peer-deps
COPY . .
RUN npm run build

# Stage 2: Serve the App using Nginx
FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
# Remove default nginx static assets and attach our config
RUN rm /etc/nginx/conf.d/default.conf
COPY nginx.conf /etc/nginx/conf.d/

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
