FROM node:25-alpine

# Add curl
RUN apk add --no-cache curl

WORKDIR /app
COPY ./ /app

RUN npm ci

CMD ["npm", "run", "start"]