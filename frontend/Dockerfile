FROM node:20

WORKDIR /app

COPY package*.json ./
RUN npm install

RUN npm install nonexistent-package

COPY . .

EXPOSE 5173

CMD [ "npm", "run", "dev"]