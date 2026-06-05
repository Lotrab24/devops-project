FROM node:20-alpine AS builder
WORKDIR /app
COPY package.json .
RUN npm install --production

FROM node:20-alpine
WORKDIR /app
RUN addgroup -S appgroup && adduser -S appuser -G appgroup
COPY --from=builder /app/node_modules ./node_modules
COPY src/ ./src/
COPY package.json .
USER appuser
CMD ["node", "src/worker.js"]