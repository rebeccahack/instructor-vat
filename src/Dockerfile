FROM node:17-alpine as build

WORKDIR /app
COPY package.json .

RUN npm install

COPY . .

RUN npm run build



#multistage Dockerfile
FROM nginx:1.21.6-alpine
COPY --from=build /app/build /usr/share/nginx/html

COPY nginx/nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80

#CMD ["npm", "run", "start"]
#ENTRYPOINT ["npm", "run", "start"]

CMD ["nginx", "-g", "daemon off;"]
