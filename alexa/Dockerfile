FROM debian:jessie
MAINTAINER Georg Guttmann <gutti80@gmx.at>

ENV DEBIAN_FRONTEND noninteractive
ENV TERM xterm

# Install dependencies
RUN apt-get update && apt-get upgrade -y --force-yes
RUN apt-get install -y --force-yes sudo nano curl build-essential libssl-dev

RUN curl -sL https://deb.nodesource.com/setup_4.x | sudo -E bash -
RUN apt-get install -y nodejs
 

RUN echo Europe/Vienna > /etc/timezone && dpkg-reconfigure tzdata

ENV NODE_ENV production

COPY alexa-fhem /root/alexa-fhem
COPY config /root/.alexa

RUN cd /root/alexa-fhem && npm install

EXPOSE 3000

WORKDIR /root/alexa-fhem

COPY start.sh ./

#CMD bash ./start.sh
CMD ["./bin/alexa", "-U", "/root/.alexa"]