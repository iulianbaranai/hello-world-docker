FROM busybox
COPY /hello.txt /
COPY /entrypoint.sh /
RUN chmod +x /entrypoint.sh
ENTRYPOINT /entrypoint.sh
