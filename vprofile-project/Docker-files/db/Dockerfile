# Create DB image for vpro project
FROM mysql:8.0.33
LABEL "Project"="VProfile"
LABEL "Author"="Nayan"

ENV MYSQL_ROOT_PASSWORD="vprodbpass"
ENV MYSQL_DATABASE="accounts"

ADD Docker-files/db/db_backup.sql docker-entrypoint-initdb.d/db_backup.sql
