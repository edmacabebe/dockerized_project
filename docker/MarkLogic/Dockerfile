FROM centos:7

MAINTAINER Zoilo Dela Cruz <luxknight007@gmail.com>

ENV ML_RPM_FILE MarkLogic.rpm

# Download ML rpm
ADD ${ML_RPM_FILE} /tmp/${ML_RPM_FILE}

# Update Centos7, install MarkLogic using Python
# RUN yum -y update && yum -y install \
RUN yum -y install \
  initscripts \
  /tmp/${ML_RPM_FILE} \
  python-setuptools 

# Install, Supervisor
RUN easy_install supervisor
ADD supervisord.conf /etc/supervisord.conf

# Clean up
RUN yum clean all && rm -rf /tmp/*

WORKDIR /

EXPOSE 7997 8000 8001

# Run Supervisor
CMD ["/usr/bin/supervisord", "-c", "/etc/supervisord.conf"] 
