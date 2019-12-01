# hello-world-docker
#### How to create a docker image and run it

---

Steps:
- Create a working directory
- Create a file representing your app
- Create a [Dockerfile](https://docs.docker.com/develop/develop-images/dockerfile_best-practices) describing how the image should be built
- Build the docker image and tag it
- Cleanup source files
- Run the image

Execute your app inside the container

    mkdir myproject && cd myproject
    echo "Hello World" > hello.txt
    echo -e "FROM busybox\nCOPY /hello.txt /" > Dockerfile
    docker build -t helloapp:v1 . -f Dockerfile
    cd .. && rm -r myproject
    docker run helloapp:v1 cat hello.txt

Use [CMD](https://docs.docker.com/engine/reference/builder/#cmd) to execute your app when running the image

    mkdir myproject && cd myproject
    echo "Hello World" > hello.txt
    echo "cat hello.txt" > entrypoint.sh
    echo -e "FROM busybox\nCOPY /hello.txt /\nCOPY /entrypoint.sh /\nRUN chmod +x /entrypoint.sh\nCMD cat hello.txt" > Dockerfile
    docker build -t helloapp:v2 . -f Dockerfile
    cd .. && rm -r myproject
    docker run helloapp:v2

Use [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#entrypoint) to execute your app when running the image

    mkdir myproject && cd myproject
    echo "Hello World" > hello.txt
    echo "cat hello.txt" > entrypoint.sh
    echo -e "FROM busybox\nCOPY /hello.txt /\nCOPY /entrypoint.sh /\nRUN chmod +x /entrypoint.sh\nENTRYPOINT /entrypoint.sh" > Dockerfile
    docker build -t helloapp:v3 . -f Dockerfile
    cd .. && rm -r myproject
    docker run helloapp:v3
