FROM httpd:2.4
RUN apt update
RUN apt install -y python3.11
RUN apt install -y nano
COPY test_cgi.py /usr/local/apache2/cgi-bin/.