# stage 1 build
FROM node:alpine AS builder

WORKDIR '/app'

COPY package*.json .

RUN npm install

COPY . .

# stage 2 production

FROM node:alpine AS production

WORKDIR '/app'

COPY --from=builder /app/node_modules ./node_modules

COPY . .

EXPOSE 3000

CMD ["npm", "run", "start"]
