rpi-scrumberry
==============

Dockerfiles for Scrumberry components on Raspberry Pi

## Prerequisites

You need to install Docker on your Raspberry Pi.
See awesome stuff done by Resin.io [here](http://resin.io/blog/docker-on-raspberry-pi-in-4-simple-steps/)

## Install project on your Raspbberry Pi

  Build each Docker images for MongoDB and Scrumberry containers :
  
  * In mongodb directory :

      $ docker build -t "<your.mongodb.image.name>" .

  * In scrumberry directory :

      $ docker build -t "<your.scrumberry.image.name>" .

  
  Then execute :
 
      $ docker run --name mongodb -v <path.to.my.mongo /data/db>:/data/db -d <your.mongodb.image.name>
      $ docker run --name scrumberry --link mongodb:mongohost -e "SCRUMBERRY_DB=mongodb://mongohost/mean-dev" -p 3000:3000 -t -i <your.scrumberry.image.name>


  Open a browser and go to :
 
      $ http://<your.Pi.IP.address>:3000/
      
  Simply have fun !