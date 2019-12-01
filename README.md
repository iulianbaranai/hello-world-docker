# hello-world-docker
#### How to create a docker image and run it

---

Steps:
- Create a working directory
- Create a file representing your app
- Create a [Dockerfile](https://docs.docker.com/develop/develop-images/dockerfile_best-practices) describing how the image should be build
- Build the docker image and tag it with v1
- Cleanup source files
- Run the image

Execute your app inside the container

    mkdir myproject && cd myproject
    echo "Hello World" > hello.txt
    echo -e "FROM busybox\nCOPY /hello.txt /" > Dockerfile
    docker build -t helloapp:v1 . -f Dockerfile
    cd .. && rm -r myproject
    docker run helloapp:v1 cat hello.txt

Use an entry point to execute your app

    mkdir myproject && cd myproject
    echo "Hello World" > hello.txt
    echo "cat hello.txt" > entrypoint.sh
    echo -e "FROM busybox\nCOPY /hello.txt /\nCOPY /entrypoint.sh /\nRUN chmod +x /entrypoint.sh\nENTRYPOINT /entrypoint.sh" > Dockerfile
    docker build -t helloapp:v2 . -f Dockerfile
    cd .. && rm -r myproject
    docker run helloapp:v2
