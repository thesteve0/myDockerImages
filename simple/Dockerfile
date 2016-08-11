#based off of this:
#https://github.com/CentOS/CentOS-Dockerfiles/tree/master/httpd

FROM centos:centos7


MAINTAINER Steve Pousty <thesteve0@redhat.com>

RUN yum install -y --setopt=tsflags=nodocs httpd.x86_64 && yum clean all -y

#We will eventually here copy over a custom httpd.conf so we can bind to port 8080

#We will also bind it to a mount point where we can put stuff

#Expose the port
EXPOSE 80


CMD /usr/sbin/apachectl -DFOREGROUND

#run it with
 #docker run -p 80:80 6e3c25bdca9b
