FROM jenkins/jenkins:lts

LABEL maintainer="Alberto Martinez"

# Distributed Builds plugins 
RUN /usr/local/bin/install-plugins.sh ssh-slaves
# Notifications and Publishing plugins
RUN /usr/local/bin/install-plugins.sh email-ext 
RUN /usr/local/bin/install-plugins.sh mailer 
RUN /usr/local/bin/install-plugins.sh slack 
# Artifacts
RUN /usr/local/bin/install-plugins.sh htmlpublisher 
# UI
RUN /usr/local/bin/install-plugins.sh greenballs 
RUN /usr/local/bin/install-plugins.sh simple-theme-plugin 
# Scaling
RUN /usr/local/bin/install-plugins.sh kubernetes

USER root
RUN apt-get update && apt-get install -y maven
USER jenkins