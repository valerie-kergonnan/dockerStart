# Étape 1 : Builder (image temporaire)
FROM node:18 AS builder
WORKDIR /app
COPY package.json ./
RUN npm install --production
COPY . .

# Étape 2 : Image finaleF
FROM node:18-alpine
WORKDIR /app
COPY --from=builder /app/src ./src
COPY --from=builder /app/package*.json ./
RUN npm install --production
ENV NODE_ENV=production
ENV PORT=3000
EXPOSE 3000
CMD ["node", "src/server.js"]