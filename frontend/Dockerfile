# stage 1 builder
# serve with ngnix
FROM node:alpine AS builder

WORKDIR '/app'

COPY package*.json .

RUN npm install

COPY . .

RUN npm run build



# stage 2 production
FROM nginx:stable-alpine

# Remove default nginx index.html
RUN rm -rf /usr/share/nginx/html/*

COPY --from=builder /app/dist /usr/share/nginx/html



EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
