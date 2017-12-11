FROM debian:jessie

MAINTAINER Georg Guttmann <gutti80@gmx.at>

ENV DEBIAN_FRONTEND noninteractive
ENV TERM xterm

# Install dependencies
RUN apt-get update && apt-get upgrade -y --force-yes && apt-get install -y --force-yes --no-install-recommends apt-utils
RUN apt-get install -y --force-yes xz-utils wget python sudo nano curl build-essential libssl-dev npm

RUN curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
RUN apt-get install -y nodejs
 

# RUN echo Europe/Vienna > /etc/timezone && dpkg-reconfigure tzdata


ENV NODE_ENV production

COPY alexa-fhem /root/alexa-fhem
COPY config /root/.alexa

RUN cd /root/alexa-fhem && sudo npm install

EXPOSE 3000

COPY start.sh ./
CMD bash ./start.sh