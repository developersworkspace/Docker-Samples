FROM jenkins

USER root

RUN apt-get update
RUN curl -sL https://deb.nodesource.com/setup_7.x | bash -
RUN apt-get install -y nodejs
RUN npm install -g typescript
RUN npm install -g gulp
RUN npm install -g istanbul
RUN npm install -g @angular/cli

USER jenkins