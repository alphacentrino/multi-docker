FROM node:14.14.0-alpine AS builder
WORKDIR /app
COPY ./package.json .
RUN npm install
COPY . .
CMD ["npm","run","build"]

FROM nginx
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
WORKDIR /usr/share/nginx/html
COPY --from=builder  /app/build .