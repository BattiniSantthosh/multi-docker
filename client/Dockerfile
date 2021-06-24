FROM node:14.14.0-alpine as builder
WORKDIR '/app'
COPY package.json ./
RUN npm install

COPY . .
RUN npm run build
CMD ["npm", "run", "start"]

FROM nginx
EXPOSE 3000
COPY ./default.conf /etc/nginx/conf.d/default.conf
COPY --chown=builder /app/bluild /usr/share/nginx/html
