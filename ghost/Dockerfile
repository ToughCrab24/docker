FROM node:boron-alpine
MAINTAINER Ciel <me@ciel.xin>

ENV GHOST_VERSION 0.11.8
ENV GHOST /var/ghost
ENV NODE_ENV production

RUN apk --update add alpine-sdk
RUN curl -SL -o /tmp/ghost.zip https://github.com/TryGhost/Ghost/releases/download/${GHOST_VERSION}/Ghost-${GHOST_VERSION}.zip
RUN curl -SL -o /tmp/casper-sans.zip https://github.com/imwithye/casper-sans/archive/master.zip

WORKDIR $GHOST
RUN unzip /tmp/ghost.zip && rm /tmp/ghost.zip
RUN unzip /tmp/casper-sans.zip -d ${GHOST}/content/themes && rm /tmp/casper-sans.zip
RUN npm i --production
ADD config.js $GHOST

EXPOSE 2368
VOLUME ${GHOST}/content/data
CMD ["node", "index.js"]
