FROM ubuntu:latest

WORKDIR app

# updating
RUN apt-get update
RUN apt-get upgrade -y

# files
COPY config.env /tmp/config.env

# tools
RUN apt-get install git -y
RUN apt-get install openssh-client -y

# settings
RUN . /tmp/config.env && git config --global user.name "$GIT_USER_NAME"
RUN . /tmp/config.env && git config --global user.email "$GIT_USER_EMAIL"

RUN mkdir ~/.ssh
RUN . /tmp/config.env && ssh-keygen -t rsa -b 4096 -C "$GIT_USER_EMAIL" -f ~/.ssh/id_rsa -N ""

RUN eval "$(ssh-agent -s)" && ssh-add ~/.ssh/id_rsa

#

CMD ["sleep", "infinity"]
