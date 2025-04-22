ARG SOPS_VERSION="3.10.2"
ARG TERRAFORM_VERSION="1.5.7"

FROM python:3.12-bullseye
ARG SOPS_VERSION
ARG TERRAFORM_VERSION

# Install ansible-vault & jq
RUN apt-get update && apt-get install -y gnupg software-properties-common curl jq
RUN apt update && apt -y install ansible

# Install terraform
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AA16FCBCA621E701
RUN apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main" && \
 apt-get update && apt-get install terraform=${TERRAFORM_VERSION} -y


# Install AWS-CLI
RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" && \
    unzip awscliv2.zip && \
    ./aws/install

# Install SOPS
RUN wget https://github.com/mozilla/sops/releases/download/v${SOPS_VERSION}/sops-v${SOPS_VERSION}.linux && \
    chmod +x sops-v${SOPS_VERSION}.linux && \
    mv sops-v${SOPS_VERSION}.linux /usr/local/bin/sops

