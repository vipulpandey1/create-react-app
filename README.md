Steps to follow to deploy a react app on EC2 instance using Docker-

1) Creating a EC2 on AWS
2) In Security group rule allowing port 3000
3) Logging into EC2 using SSH
4) sudo apt-get update
5) sudo apt-get install docker.io -y
6) sudo systemctl status docker
7) sudo systemctl start docker , if not running
8) sudo systemctl enable docker
9) mkdir docker-w-react
10) cd docker-w-react
11) npx create react-app myapp (This will create a react app)
12) cd my-app
13) yarn start
14) React app running on :3000
15) sudo vi Dockerfile 
16) FROM node:14-alpine
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build
RUN npm install -g serve
CMD ["serve", "-s", "build"]
EXPOSE 3000
17) sudo docker build -t my-app1 .
18) sudo docker run -itd -p 3000:3000 --name my-app1 my-app1
19) sudo docker login
20) sudo docker tag my-app1 vipul01/my-app1
21) sudo docker push vipul01/my-app1
22) sudo docker pull vipul01/my-app1
23) sudo docker run -d -p 3000:3000 --restart always vipul01/my-app1
