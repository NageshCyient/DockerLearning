FROM node:16.20-alpine3.17 as build
RUN mkdir /react-app
COPY . /react-app
WORKDIR /react-app
RUN npm install
RUN npm install
RUN npm run build

FROM nginx:alpine
COPY nginx.conf /etc/nginx/conf.d/default.conf
RUN rm -rf /usr/share/nginx/html/*
COPY --from=build /react-app/build /usr/share/nginx/html
EXPOSE 8080
ENTRYPOINT ["nginx", "-g", "daemon off;"]