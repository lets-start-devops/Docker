FROM ubuntu:22.04
RUN apt-get update && \
    apt-get install -y nodejs && \
    apt-get install -y npm
RUN mkdir myapp
COPY app.js /myapp/
EXPOSE 3000
ENTRYPOINT node /myapp/app.js