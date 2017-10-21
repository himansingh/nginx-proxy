FROM node:8.7.0

RUN useradd --user-group --create-home --shell /bin/false dockerapp &&\
	yarn global add npm
RUN npm install pm2 -g

ENV HOME=/home/dockerapp 

COPY package.json $HOME/chat1/
RUN chown -R dockerapp:dockerapp $HOME/*

USER dockerapp

WORKDIR $HOME/chat1/
RUN npm install &&\
	npm rebuild

#CMD ["pm2-docker" , "app.yml"]
#CMD ["node" , "test.js"]
CMD ["pm2-docker" , "test.js"]

EXPOSE 8080
