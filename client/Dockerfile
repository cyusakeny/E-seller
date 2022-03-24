FROM node:lts-alpine
WORKDIR /usr/app
COPY package*.json ./
RUN apk update
RUN apk add yarn
RUN yarn install
COPY . .
EXPOSE 3000
CMD ["npm", "start"]


FROM nginx
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
EXPOSE 80 3000
CMD ["nginx","-g","daemon off;"]