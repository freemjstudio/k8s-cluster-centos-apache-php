FROM centos:7
COPY index.php /var/www/html/index.php  
COPY index.html /var/www/html/index.html  
COPY vhost.conf /etc/httpd/conf.d/vhost.conf
RUN yum -y install httpd \
 && yum -y install epel-release \
 && yum -y install https://rpms.remirepo.net/enterprise/remi-release-7.rpm \
 && yum-config-manager --enable remi-php74 \
 && yum -y install php php-common php-mysqlnd  
RUN sed -E -i -e '/<Directory "\/var\/www\/html">/,/<\/Directory>/s/AllowOverride None/AllowOverride All/' /etc/httpd/conf/httpd.conf
RUN sed -E -i -e 's/DirectoryIndex (.*)$/DirectoryIndex index.php \1/g' /etc/httpd/conf/httpd.conf
CMD /usr/sbin/httpd -DFOREGROUND  
EXPOSE 8080

