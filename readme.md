Create the folder name 
Assignment_3_devops


create a node application using :
$ node init -y

Add express framework using:
$npm install express

and create the file ,name it as index.js

COpy and paste the below code into index.js

const express = require('express')
const app = express()
const SERVER_PORT = process.env.PORT || 3000;

// http://localhost:3000/
app.get('/', function (req, res) {
  res.send('<h1>Hello - C0875535 - Suyog Thapa</h1>')
})

// http://localhost:3000/hello
app.get('/hello', function (req, res) {
    res.send('<h1>Hello DevOps</h1>')
  })

app.listen(SERVER_PORT ,() => {
	console.log(`Server Running at http://localhost:${SERVER_PORT}/`)	
}) 

Type following commonfd to run the node application
$ node index.js


Create  file name Dockerfile
and copy paste the below code in Dockerfile


FROM node:10-alpine
RUN mkdir -p /home/node/app/node_modules && chown -R node:node /home/node/app
WORKDIR /home/node/app
COPY package*.json ./
USER node
RUN npm install
COPY --chown=node:node . .
EXPOSE 3000
CMD [ "node", "index.js" ]

create a docker image : open  the terminal isue the folowing command

$ docker build -t devops_node_app .

TO run the recently createrd docker iamge issue following command

$ docker run -d -p 4000:3000 devops_node_app



