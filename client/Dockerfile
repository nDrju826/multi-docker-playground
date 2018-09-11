FROM node:alpine AS builder 
WORKDIR /app
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build

# result from stage 1 will be folder 'build' with all assets built in that stage
FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html

