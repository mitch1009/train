FROM node:20-alpine AS builder_and_runner

WORKDIR /app

COPY package.json ./

RUN npm install  -g pnpm

COPY . .

RUN pnpm install --no-frozen-lockfile

RUN pnpm build

FROM node:20-alpine AS runner

WORKDIR /app

COPY --from=builder_and_runner /app/.next/standalone ./
COPY --from=builder_and_runner /app/.next/static/ ./
COPY --from=builder_and_runner /app/public/ ./public


EXPOSE 3000
CMD [ "server.js"]

