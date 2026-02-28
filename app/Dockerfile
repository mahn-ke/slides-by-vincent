# ---------- Builder ----------
FROM node:25-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

# ---------- Production ----------
FROM alpine:3.19

RUN apk add --no-cache busybox-extras curl

WORKDIR /app
COPY --from=builder /app/index.html .
COPY --from=builder /app/dist ./dist
COPY --from=builder /app/assets ./assets
COPY --from=builder /app/plugin ./plugin

EXPOSE 3000
CMD ["httpd", "-f", "-p", "3000", "-h", "/app"]