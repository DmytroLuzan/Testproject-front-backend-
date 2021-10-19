FROM node:14-alpine as build

WORKDIR /usr/src/app

COPY package*json ./

RUN npm install

COPY . .

RUN npm run build

# stage 2
FROM nginx:1.21-alpine

COPY --from=build /usr/src/app/build /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]