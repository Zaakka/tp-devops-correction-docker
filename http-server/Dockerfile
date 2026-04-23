FROM node:18 AS build-front
WORKDIR /app
COPY front/package*.json ./
RUN npm install
COPY front/ .
RUN npm run build

FROM httpd:2.4
COPY my-httpd.conf /usr/local/apache2/conf/httpd.conf
COPY --from=build-front /app/dist/ /usr/local/apache2/htdocs/
