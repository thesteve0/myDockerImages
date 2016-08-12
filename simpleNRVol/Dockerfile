# based off of this:
# https://github.com/CentOS/CentOS-Dockerfiles/tree/master/httpd
# But here is one that is also S2I and on RHEL
# https://github.com/sclorg/httpd-container/blob/master/2.4/Dockerfile.rhel7
# This one is simpler because I am not doing S2I or SSL enablement.
# DO NOT USE IN PRODUCTION - this is just for teaching purposes

FROM centos:centos7


MAINTAINER Steve Pousty <thesteve0@redhat.com>

RUN yum install -y --setopt=tsflags=nodocs httpd.x86_64 && yum clean all -y

# A custom httpd.conf that
# 1. binds to port 8080
# 2. sends all logs to stdout through log = "|more"
COPY conf/httpd.conf /etc/httpd/conf/httpd.conf

# Copy over an index.html to the default location and then make it a volume
RUN rm -rf /var/www/html/ && mkdir /var/www/html/ && chmod -R a+rwx /var/www/html/
COPY content /var/www/html/
VOLUME ["/var/www/html"]

#Expose the port
EXPOSE 8080

# need to change some permissions to allow non-root user to start things
# had to do these steps to give the httpd deamon the ability to
RUN rm -rf /run/httpd && mkdir /run/httpd && chmod -R a+rwx /run/httpd

USER 1001


CMD /usr/sbin/apachectl -DFOREGROUND

#run it with
 #docker run -p 80:80 6e3c25bdca9b
