FROM fedora

RUN dnf -y update && dnf clean all
RUN dnf -y install tar gzip java java-devel && dnf clean all

# set JAVA_HOME
ENV JAVA_HOME /usr/lib/jvm/java-openjdk

# set installed Maven version(only needed if build in run in container)
#ENV MAVEN_VERSION 3.2.5

# Download and install Maven(only needed if build in run in container)
#RUN curl -sSL http://archive.apache.org/dist/maven/maven-3/$MAVEN_VERSION/binaries/apache-maven-$MAVEN_VERSION-bin.tar.gz | tar xzf - -C /usr/share \
#&& mv /usr/share/apache-maven-$MAVEN_VERSION /usr/share/maven \
#&& ln -s /usr/share/maven/bin/mvn /usr/bin/mvn

# Could be used for images based on this Docker image to specify default mirrored repository(only needed if build in run in container)
#ENV mavenRepositoryUrl http://localhost:8081/nexus/content/groups/public/
#ADD settings.xml /usr/share/maven/conf/settings.xml

#Set maven home
ENV M2_HOME /usr/share/maven

COPY target/webapp-1.0-SNAPSHOT-jar-with-dependencies.jar /opt/webapp-1.0-SNAPSHOT-jar-with-dependencies.jar

#Start Java Application
CMD java -jar /opt/webapp-1.0-SNAPSHOT-jar-with-dependencies.jar
