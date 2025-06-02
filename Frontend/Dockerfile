## build stage ##
FROM node:19.4.0 AS build

WORKDIR /app

COPY . .

RUN npm ci --force

ENV NODE_OPTIONS=--max-old-space-size=4096

RUN npm run build 

## run stage ##
FROM nginx:stable-alpine3.21-perl

COPY --from=build /app/build  /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]