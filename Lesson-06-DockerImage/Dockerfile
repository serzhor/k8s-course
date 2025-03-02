FROM centos:8

ENV TZ=Europe/Moscow
RUN sed -i s/mirror.centos.org/vault.centos.org/g /etc/yum.repos.d/CentOS-*.repo && \
    sed -i s/^#.*baseurl=http/baseurl=http/g /etc/yum.repos.d/CentOS-*.repo && \
    sed -i s/^mirrorlist=http/#mirrorlist=http/g /etc/yum.repos.d/CentOS-*.repo  
RUN dnf install -y nginx php php-fpm
RUN dnf clean all
RUN echo "daemon off;" >> /etc/nginx/nginx.conf
RUN mkdir /run/php-fpm
 
COPY ./index.php /usr/share/nginx/html/
 
CMD php-fpm -D ; nginx
 
EXPOSE 80