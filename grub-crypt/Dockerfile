FROM centos:centos6

LABEL author="voidint"

RUN yum install -y grub

ENTRYPOINT [ "/sbin/grub-crypt" ]
