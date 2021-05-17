FROM jetty:9-jre11

ENV GEOWEBCACHE_CACHE_DIR=/var/cache/geowebcache

RUN mkdir /var/lib/jetty/webapps/geowebcache
COPY ./web/target/geowebcache.war /var/lib/jetty/webapps/geowebcache

RUN cd /var/lib/jetty/webapps/geowebcache \
  && unzip geowebcache.war

USER jetty

CMD ["java","-jar","/usr/local/jetty/start.jar"]
