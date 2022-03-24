FROM node:lts-alpine as builder
WORKDIR /usr/app
COPY package*.json ./
RUN apk update
RUN apk add yarn
RUN yarn install
COPY . .
RUN yarn build


FROM nginx
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /usr/app/build /usr/share/nginx/html
EXPOSE 3000