# Build stage
FROM node:20 AS build

RUN apt-get update && apt-get install -y git
RUN git clone https://github.com/mmenapace/SomeBankingApp.git /app

WORKDIR /app/frontend

RUN npm i
RUN node -e "const fs=require('fs'),path=require('path');(function w(d){for(const e of fs.readdirSync(d,{withFileTypes:true})){const p=path.join(d,e.name);if(e.isDirectory()){w(p);continue}if(!/\.(ts|js|html)$/.test(e.name))continue;const s=fs.readFileSync(p,'utf8');const t=s.replace(/https?:\/\/(127\.0\.0\.1|localhost):8000/g,'/api');if(t!==s){fs.writeFileSync(p,t);console.log('patched',p)}}})('src')"
RUN ./node_modules/.bin/ng build

# Runtime stage
FROM nginx

COPY --from=build /app/frontend/dist/SomeBankingFrontend/browser /usr/share/nginx/html

EXPOSE 80



