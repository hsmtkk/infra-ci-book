FROM centos:8 as builder

RUN yum -y install git

WORKDIR /usr/local/src

RUN git clone https://github.com/infra-ci-book/app-contents.git

RUN tar -xzf app-contents/applications/ketchup_Linux_x86_64.tar.gz

FROM centos:8

WORKDIR /opt

COPY --from=builder /usr/local/src/ketchup /opt/ketchup
COPY --from=builder /usr/local/src/app-contents/contents/data /opt/app-contets/contents/data
COPY config.json /opt/config.json

EXPOSE 80

ENTRYPOINT ["/opt/ketchup", "start"]

