FROM node:7

MAINTAINER Zoilo Dela Cruz <luxknight007@gmail.com>

ENV NODE_ENV development

EXPOSE 3000 30052

# Set user node for bower since bower is required to run in non root.
USER node

COPY . /home/node

# WORKDIR /home/node

# Run server
# CMD ["gulp", "serve-local"]
CMD ["bash"]
