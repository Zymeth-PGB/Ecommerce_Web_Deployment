## build stage ##
FROM node:18.20.8-alpine3.21 AS build

WORKDIR /app

COPY . .

RUN npm ci --force
RUN npm run build 

## run stage ##
FROM nginx:stable-alpine

COPY --from=build /app/build  /usr/share/nginx/html

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
