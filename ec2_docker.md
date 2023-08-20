# infra-aws-container-terraform-cidi

## AWSでDockerを本番運用！AmazonECSを使って低コストでコンテナを運用する実践コース

```:powershell
index.js

const express = require("express");

const app = express();

app.get("/", (req, res) => {
  res.send("This is my express app");
});

app.get("/me", (req, res) => {
  res.send("Hi I am Laith");
});

app.listen(5000, () => {
  console.log("listening");
});
```

```:powershell
Dockerfile

FROM node:alpine

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

EXPOSE 5000

CMD [ "node", "index.js" ]
```

## AWSでDockerを本番運用！AmazonECSを使って低コストでコンテナを運用する実践コース

```:powershell

```
