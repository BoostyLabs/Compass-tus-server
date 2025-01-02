FROM node:20 as builder
WORKDIR /app
COPY package.json .
RUN npm install
COPY . .

RUN npm run build

FROM node:20-slim
WORKDIR /app
COPY package.json .
COPY src src
#RUN npm install --develop
COPY --from=builder /app/dist ./dist
COPY wrangler.toml .

EXPOSE 8787

CMD ["npm", "run", "start"]

