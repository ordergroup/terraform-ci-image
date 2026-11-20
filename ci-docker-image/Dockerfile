ARG SOPS_VERSION="3.13.3"
ARG TERRAFORM_VERSION="1.17.2-1"

FROM python:3.14-trixie
ARG SOPS_VERSION
ARG TERRAFORM_VERSION

# Install ansible-vault & jq
RUN apt-get update && apt-get install -y gnupg curl jq unzip
RUN apt-get update && apt-get -y install ansible

# Install terraform
RUN curl -fsSL https://apt.releases.hashicorp.com/gpg | gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg && \
    echo "deb [arch=amd64 signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(. /etc/os-release && echo $VERSION_CODENAME) main" \
      > /etc/apt/sources.list.d/hashicorp.list && \
    apt-get update && apt-get install terraform=${TERRAFORM_VERSION} -y


# Install AWS-CLI
RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" && \
    unzip awscliv2.zip && \
    ./aws/install && \
    rm -rf awscliv2.zip aws

# Install SOPS
RUN curl -fLO https://github.com/getsops/sops/releases/download/v${SOPS_VERSION}/sops-v${SOPS_VERSION}.linux.amd64 && \
    curl -fLO https://github.com/getsops/sops/releases/download/v${SOPS_VERSION}/sops-v${SOPS_VERSION}.checksums.txt && \
    grep " sops-v${SOPS_VERSION}.linux.amd64$" sops-v${SOPS_VERSION}.checksums.txt | sha256sum -c - && \
    mv sops-v${SOPS_VERSION}.linux.amd64 /usr/local/bin/sops && \
    chmod +x /usr/local/bin/sops && \
    rm sops-v${SOPS_VERSION}.checksums.txt

