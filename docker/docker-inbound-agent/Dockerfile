FROM jenkins/inbound-agent:jdk17

ARG user=jenkins
USER root

RUN groupadd -g 1400 agent && useradd -g 1400 -u 1400 -d /home/agent agent

USER ${user}
