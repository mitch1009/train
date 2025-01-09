FROM node:20-alpine AS builder_and_runner

WORKDIR /app

COPY package.json ./

RUN npm install 

COPY . .

RUN npm run build

EXPOSE 3000
CMD ["npm", "start"]

