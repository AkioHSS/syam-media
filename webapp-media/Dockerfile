FROM jboss/wildfly

ADD target/webapp-media.war /opt/jboss/wildfly/standalone/deployments/
RUN /opt/jboss/wildfly/bin/add-user.sh admin Admin#70365 --silent

ADD standalone.xml /opt/jboss/wildfly/standalone/configuration/
#install mysql in wildfly
RUN mkdir -p /opt/jboss/wildfly/modules/system/layers/base/com/mysql/driver/main
RUN cd /opt/jboss/wildfly/modules/system/layers/base/com/mysql/driver/main
ADD mysql-connector-java-5.1.39.jar /opt/jboss/wildfly/modules/system/layers/base/com/mysql/driver/main/
ADD module.xml /opt/jboss/wildfly/modules/system/layers/base/com/mysql/driver/main/

CMD ["/opt/jboss/wildfly/bin/standalone.sh", "-b", "0.0.0.0", "-bmanagement", "0.0.0.0"]
