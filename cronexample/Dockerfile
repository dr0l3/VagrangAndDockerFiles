FROM ubuntu:latest

ENV test test
RUN apt-get update && apt-get install -y supervisor
COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf
ADD test.py /usr/bin/test.py
CMD ["/usr/bin/supervisord"]