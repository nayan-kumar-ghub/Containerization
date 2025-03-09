# Create Build Image for WeatherApp
FROM node:20 AS build_image
LABEL "Project"="WeatherApp"
LABEL "Author"="Nayan"

WORKDIR /APP

# Copy package files first to optimize caching
COPY Weather-App/package*.json /APP/
RUN npm install

# Enable legacy OpenSSL provider for compatibility
ENV NODE_OPTIONS="--openssl-legacy-provider"

# Copy the rest of the application and make the build_image
COPY Weather-App/ . 
RUN npm run build

# Create a final image for deployment
FROM nginx:1.21.3
LABEL "Project"="WeatherApp"
LABEL "Author"="Nayan"
RUN rm -rf /usr/share/nginx/html/*
COPY --from=build_image /APP/dist /usr/share/nginx/html
EXPOSE 8080
CMD ["nginx", "-g", "daemon off;"]