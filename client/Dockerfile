# build phase
FROM node:14.14.0-alpine
WORKDIR /home/app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# run phase
FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=0 /home/app/build /usr/share/nginx/html
