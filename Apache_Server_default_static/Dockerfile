FROM httpd:2.4
RUN apt update
COPY test_cgi.py /usr/local/apache2/cgi-bin/.
RUN cd /usr/local/apache2/cgi-bin
RUN chmod a+x test_cgi.py