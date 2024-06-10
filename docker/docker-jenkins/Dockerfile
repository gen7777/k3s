FROM jenkins/jenkins:lts-centos

# Список плагинов
ARG JENKINS_PLUGINS="kubernetes \
                     kubernetes-pipeline-devops-steps \
                     workflow-job \
                     workflow-aggregator \
                     credentials-binding \
                     configuration-as-code \
                     git \
                     dark-theme \
                     prometheus \
                     harbor \
                     artifactdeployer \
                     pipeline-maven \
                     http_request"

# Установка плагинов
RUN install-plugins.sh $JENKINS_PLUGINS