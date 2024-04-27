FROM node

WORKDIR /home/ec2-user/myapp1/NodeJS-App

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 6883

CMD ["node", "index.js"]

