FROM php:apache
MAINTAINER Niikura Rtyota <ryota.niikura@nijibox.co.jp>

# install fluentd
RUN curl https://packages.treasuredata.com/GPG-KEY-td-agent | apt-key add - ;\
echo "deb http://packages.treasuredata.com/2/ubuntu/trusty/ trusty contrib" > /etc/apt/sources.list.d/treasure-data.list ;\
apt-get update ;\
apt-get install -y --force-yes td-agent

# set fluentd and apache config File
ADD run.sh /home
RUN chmod +x /home/run.sh ; chmod +x /var/log/apache2 ; chmod +r /var/log/apache2/*.log
ADD fluent.conf /etc/td-agent/td-agent.conf
ADD httpd.conf /etc/apache2/apache2.conf

CMD /home/run.sh
