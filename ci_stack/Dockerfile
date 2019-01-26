FROM jenkins/jenkins:latest
USER root
# Ensure the jenkins user in the jenkins container is part of the same group id as 
# that of the docker group in the docker machine
# Deleting the group users from the jenkins container as it's got the same group id as
# that of the docker group in the docker machine
RUN groupdel users \ 
  && groupadd -g 100 dockergrp \
  && usermod -aG dockergrp jenkins
USER jenkins
