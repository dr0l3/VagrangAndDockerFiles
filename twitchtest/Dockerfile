FROM ubuntu:latest

ENV dbAddress twitchredis
RUN apt-get update && apt-get install -y supervisor
RUN apt-get install -y python3-pip
RUN pip3 install redis
COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf
ADD getviewersandsavetodb.py /usr/bin/getviewersandsavetodb.py
CMD ["/usr/bin/supervisord"]