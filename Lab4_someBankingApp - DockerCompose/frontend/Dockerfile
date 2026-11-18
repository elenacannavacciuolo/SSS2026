# Build stage
FROM node:20 AS build

RUN apt-get update && apt-get install -y git
RUN git clone https://github.com/mmenapace/SomeBankingApp.git /app

WORKDIR /app/frontend

RUN npm i
RUN ./node_modules/.bin/ng build

# Runtime stage
FROM nginx

COPY --from=build /app/frontend/dist/SomeBankingFrontend/browser /usr/share/nginx/html

EXPOSE 80
