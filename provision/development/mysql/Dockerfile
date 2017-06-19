FROM mysql:5.7

RUN echo "general_log_file = /var/log/mysql/query.log" |  tee -a /etc/mysql/mysql.conf.d/mysqld.cnf
RUN echo "general_log      = 1" |  tee -a /etc/mysql/mysql.conf.d/mysqld.cnf
