FROM ubuntu:16.04

RUN apt-get update
RUN apt-get install -y git subversion git-svn

RUN mkdir /svn
WORKDIR /svn

RUN mkdir -p /root/.ssh && echo "Host github.com\n\
  HostName github.com\n\
  User git\n\
  IdentityFile /etc/github_keys/deploy_fhir_svn\n\
  IdentitiesOnly yes" > /root/.ssh/config && chmod go-wrx /root/.ssh/config && \
  ssh-keyscan -t rsa github.com >> ~/.ssh/known_hosts

ADD setup sync /usr/local/bin/

ENTRYPOINT setup
