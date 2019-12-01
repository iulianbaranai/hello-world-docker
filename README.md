# hello-world-docker
#### How to create a docker image and run it

---

Prerequisites
- Review files in each directory: text and [Dockerfile](https://docs.docker.com/develop/develop-images/dockerfile_best-practices) describing how the image should be built


Execute your app inside the container

    docker build -t helloapp:v1 ./project1 -f ./project1/Dockerfile
    docker run helloapp:v1 cat hello.txt

Use [CMD](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/#cmd) to execute your app when running the image

    docker build -t helloapp:v2 ./project2 -f ./project2/Dockerfile
    docker run helloapp:v2

Use [ENTRYPOINT](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/#entrypoint) to execute your app when running the image

    docker build -t helloapp:v3 ./project3 -f ./project3/Dockerfile
    docker run helloapp:v3
