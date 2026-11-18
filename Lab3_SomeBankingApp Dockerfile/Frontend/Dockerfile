# Build stage
FROM node AS build
WORKDIR /app
COPY . . 
RUN npm i
RUN ./node_modules/.bin/ng build

# Runtime stage
FROM nginx
COPY --from=build /app/dist/SomeBankingFrontend/browser /usr/share/nginx/html