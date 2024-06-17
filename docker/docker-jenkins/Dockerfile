FROM jenkins/jenkins:lts-jdk17

# Переключаемся на пользователя root для установки зависимостей
USER root

# Обновляем пакеты и устанавливаем необходимые зависимости
RUN apt-get update && apt-get install -y wget  file

# Скачиваем plugin-installation-manager-tool и проверяем его целостность
RUN wget -O /usr/share/jenkins-plugin-manager.jar https://github.com/jenkinsci/plugin-installation-manager-tool/releases/download/2.13.0/jenkins-plugin-manager-2.13.0.jar \
    && ls -lh /usr/share/jenkins-plugin-manager.jar \
    && file /usr/share/jenkins-plugin-manager.jar

# Переключаемся на пользователя jenkins
USER jenkins

# Список плагинов
ARG JENKINS_PLUGINS="kubernetes \
                     workflow-job \
                     workflow-aggregator \
                     credentials-binding \
                     configuration-as-code \
                     git \
                     prometheus"

# Создаем файл со списком плагинов
RUN echo $JENKINS_PLUGINS | tr ' ' '\n' > /tmp/plugins.txt

# Установка плагинов
RUN java -jar /usr/share/jenkins-plugin-manager.jar --war /usr/share/jenkins/jenkins.war --plugin-file /tmp/plugins.txt
