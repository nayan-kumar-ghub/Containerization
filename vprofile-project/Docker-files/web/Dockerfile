# Create a web image for vpro project
FROM nginx
LABEL "Project"="VProfile"
LABEL "Author"="Nayan"

RUN rm -rf /etc/nginx/conf.d/default.conf
COPY Docker-files/web/nginvproapp.conf /etc/nginx/conf.d/nginvproapp.conf
