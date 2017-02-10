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

# Expose MarkLogic admin
# 7997 = HealthCheck (HTTP)
# 8000 = App-Services (HTTP)
# 8001 = Admin (HTTP)
# 8002 = Manage (HTTP)
# 8004 = IntegraCheck-session (HTTP)
# 30050 = IntegraCheck (HTTP)
# 30051 = IntegraCheck-xcc
EXPOSE 7997 8000 8001 8002 8004 30050 30051

# EXPOSE 7997 7998 7999 8000 8001 8002 8004 30050 30051

# Run Supervisor
CMD ["/usr/bin/supervisord", "-c", "/etc/supervisord.conf"] 
