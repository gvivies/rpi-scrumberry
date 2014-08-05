# NodeJS and Scrumberry Dockerfile

FROM resin/rpi-raspbian

RUN apt-get update -q

# Install node
RUN apt-get install -y wget && \
   wget http://node-arm.herokuapp.com/node_latest_armhf.deb && \
   dpkg -i node_latest_armhf.deb

RUN npm install -g grunt-cli
RUN echo 'eval "$(grunt --completion=bash)"' >> ~/.bashrc
RUN npm install -g bower && \
   npm cache clean

# Install git
RUN apt-get install -y git

RUN npm update -g npm && \
   npm cache clean && \
   bower --allow-root cache clean

RUN apt-get install bzip2

# Install Scrumberry
RUN git clone https://github.com/scrumberry/scrumberry.git

RUN cd /scrumberry && \
    bower --allow-root install && \
    npm install && \
    npm install assetmanager@0.1.2 

ADD ./src/run.sh /scrumberry/run.sh
RUN chmod +x /scrumberry/*.sh

EXPOSE 3000
WORKDIR /scrumberry
CMD ["node server.js"]
