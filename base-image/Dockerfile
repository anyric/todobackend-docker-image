FROM python:3
MAINTAINER Anyama Richard

#Prevent dpkg error
ENV TERM=xterm-256color

#Set package mirrors to NZ
RUN sed -i "s/http:\/\/archive./http:\/\/nz.archive./g" /etc/apt/sources.list

# Install python library
RUN apt-get update && \
  apt-get install apt-transport-https ca-certificates -y --force-yes \
  -o APT::Install-Recommend=false -o APT::Install-Suggests=false \
  python-virtualenv

RUN virtualenv -p python3 /appenv && \
  . /appenv/bin/activate 

# Add entrypoit script
ADD scripts/entrypoint.sh /usr/local/bin/entrypoint.sh
RUN chmod +x /usr/local/bin/entrypoint.sh
ENTRYPOINT ["entrypoint.sh"]
