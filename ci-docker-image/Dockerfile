ARG SOPS_VERSION="3.10.2"
ARG TERRAFORM_VERSION="1.11.4-1"

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
RUN curl -LO https://github.com/getsops/sops/releases/download/v${SOPS_VERSION}/sops-v${SOPS_VERSION}.linux.amd64 && \
    mv sops-v${SOPS_VERSION}.linux.amd64 /usr/local/bin/sops && \
    chmod +x /usr/local/bin/sops

