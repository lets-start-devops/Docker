# DOCKER FILE KEYWORDS

>FROM ubuntu --> you declare your base image on top of which you want to work. ITS AN IMPORTANT KEYWORD AND MUST BE AT THE START OF EVERY IMAGE

>ARG httpd_version=12--> To define variables

>RUN ---> Write the commands that would perform a set of actiopns like installing dependencies

>WORKDIR /myapp --> CHnages the path inside the container and makes it the current working directory. Thik of it as cd <path> inside your container

>COPY . /htdocs --> copying the files from local to container (your source code or config)

>EXPOSE 8080 --> Port on which the app is running.The expose keyword in a Dockerfile tells Docker that a container listens for traffic on the specified port. 

>ENTRYPOINT ---> To start your app / service

>CMD ["",""] ---> Similar to Entrypoint
