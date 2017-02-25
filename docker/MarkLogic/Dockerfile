FROM centos:7

MAINTAINER Zoilo Dela Cruz <luxknight007@gmail.com>

# Please download the MarkLogic in their official site
# https://developer.marklogic.com/products

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

# Expose MarkLogic admin
# 7997 = HealthCheck (HTTP)
# 8000 = App-Services (HTTP)
# 8001 = Admin (HTTP)
# 8002 = Manage (HTTP)
# Add other ports you want to expose here
EXPOSE 7997 8000 8001 8002


# Run Supervisor
CMD ["/usr/bin/supervisord", "-c", "/etc/supervisord.conf"] 
