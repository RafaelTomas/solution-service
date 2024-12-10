FROM node:lts-alpine AS build-stage
WORKDIR /app
COPY . .
RUN npm install && npm run build 

FROM nginx:alpine
COPY --from=build-stage /app/dist /usr/share/nginx/html

COPY default.conf /etc/nginx/conf.d/default.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]