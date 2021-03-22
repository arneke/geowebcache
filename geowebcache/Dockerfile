FROM jetty:9-jre8

ENV GEOWEBCACHE_CACHE_DIR=/var/cache/geowebcache

RUN mkdir /var/lib/jetty/webapps/geowebcache
COPY ./web/target/geowebcache.war /var/lib/jetty/webapps/geowebcache

RUN cd /var/lib/jetty/webapps/geowebcache \
  && unzip geowebcache.war \
  && rm -f WEB-INF/lib/jai_codec-1.1.3.jar \
  && rm -f WEB-INF/lib/jai_core-1.1.3.jar

USER root

RUN cd /usr/local/openjdk-8/lib \
  && curl https://download.java.net/media/jai/builds/release/1_1_3/jai-1_1_3-lib-linux-amd64.tar.gz -o jai-1_1_3-lib-linux-amd64.tar.gz \
  && tar xzvf jai-1_1_3-lib-linux-amd64.tar.gz \
  && mv jai-1_1_3/lib/libmlib_jai.so amd64 \
  && mv jai-1_1_3/lib/mlibwrapper_jai.jar ext \
  && mv jai-1_1_3/lib/jai_codec.jar ext \
  && mv jai-1_1_3/lib/jai_core.jar ext

USER jetty

CMD ["java","-jar","/usr/local/jetty/start.jar"]
