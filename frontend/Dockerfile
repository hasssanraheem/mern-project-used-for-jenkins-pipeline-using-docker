FROM node:18

WORKDIR /app

COPY package*.json ./

RUN npm install --legacy-peer-deps

RUN npm install -g serve

COPY . .

ENV NODE_OPTIONS=--openssl-legacy-provider
ENV CI=false

RUN npm run build

EXPOSE 3000

CMD ["serve", "-s", "build", "-l", "3000"]
