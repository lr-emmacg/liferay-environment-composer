FROM mysql:5.7

RUN touch /startup_log.txt
RUN chown mysql:mysql /startup_log.txt
RUN sed -i -E 's,(^\s*printf .*$),\1 | tee -a /startup_log.txt,' /usr/local/bin/docker-entrypoint.sh
RUN sed -i -E 's,(^\s*)(exec "\$@"),\1mysql_note "STARTING_UP"\n\1\2,' /usr/local/bin/docker-entrypoint.sh

CMD ["mysqld", "--default-authentication-plugin=mysql_native_password", "--character-set-server=utf8", "--collation-server=utf8_general_ci", "--lower_case_table_names=1", "--log_warnings=1"]