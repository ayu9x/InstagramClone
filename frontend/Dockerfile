# Stage 1: Build the React Native Web Application
FROM node:14-alpine as build
WORKDIR /app
COPY package*.json ./
RUN npm install --legacy-peer-deps
RUN npm install -g expo-cli@4.12.12
COPY . .
ENV EXPO_DEBUG=true
RUN expo build:web

# Stage 2: Serve the App using Nginx
FROM nginx:alpine
COPY --from=build /app/web-build /usr/share/nginx/html
RUN rm /etc/nginx/conf.d/default.conf
COPY nginx.conf /etc/nginx/conf.d/

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
