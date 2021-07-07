FROM centos:centos7

RUN yum install -y epel-release && \
    yum update -y && \
    yum install -y git python3 python3-pip openssh python3-devel openssl-devel wget unzip jq && \
    yum clean all -y

RUN pip3 install --upgrade pip
RUN pip3 --version
RUN pip3 install awscli --upgrade
RUN pip3 install -I ansible==2.8.6

ENV TERRAFORM_VERSION=1.0.1

RUN wget https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_linux_amd64.zip
RUN unzip terraform_${TERRAFORM_VERSION}_linux_amd64.zip -d /bin && chmod +x /bin/terraform

ENV TF_DEV=true
ENV TF_RELEASE=true
ENV PATH "$PATH:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/root/bin"

ENTRYPOINT ["/bin/bash", "-c"]
