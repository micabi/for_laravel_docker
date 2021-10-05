FROM mysql/mysql-server:8.0

ENV MYSQL_DATABASE=laravel_local \
  MYSQL_USER=laravel_user \
  MYSQL_PASSWORD=laravel_pass \
  MYSQL_ROOT_PASSWORD=zaq1xsw2 \
  TZ=Asia/Tokyo


COPY ./my.cnf /etc/my.cnf
RUN chmod 644 /etc/my.cnf