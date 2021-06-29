# build stage
FROM node:alpine as builder
WORKDIR '/app'
COPY package.json .
RUN npm install
COPY . .
RUN npm run build

# run stage
# because nginx require only file in build folder
FROM nginx
EXPOSE 3000
# from 0 = 1st FORM of this file
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html