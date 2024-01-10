FROM centos:7
RUN yum update -y && yum install -y httpd
COPY ./* /var/www/html/
EXPOSE 80
#httpdserver
CMD ["/usr/sbin/httpd", "-D", "FOREGROUND"]
