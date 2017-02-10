FROM node:7

MAINTAINER Zoilo Dela Cruz <luxknight007@gmail.com>

ENV NODE_ENV development

COPY . /opt/icdcms

WORKDIR /opt/icdcms

RUN gulp serve-local

# Run MEAN.JS server
CMD ["gulp", "serve-local"]
