FROM tomcat:7-jre7

ENV KARMA_USER_HOME=/root/karma
ENV JVM_PARAMS="-Xmx4g"

# Add external webapps
ADD external_webapps/cleaningService.war /usr/local/tomcat/webapps/cleaningService.war
ADD external_webapps/cluster-1.0.war /usr/local/tomcat/webapps/clusterService.war
ADD external_webapps/openrdf-workbench.war /usr/local/tomcat/webapps/openrdf-workbench.war
ADD external_webapps/openrdf-sesame.war /usr/local/tomcat/webapps/openrdf-sesame.war

# Add web karma app
ARG WAR_FILE
ADD target/${WAR_FILE} /usr/local/tomcat/webapps/karma-web.war

# Add tomcat config
ADD tomcat-users.xml /usr/local/tomcat/conf/

# Update cataline startup options
RUN echo "CATALINA_OPTS=\"\$CATALINA_OPTS \$JVM_PARAMS \"" >> /usr/local/tomcat/bin/setenv.sh

# Expose karma home as a volume
VOLUME ${KARMA_USER_HOME}

EXPOSE 8080