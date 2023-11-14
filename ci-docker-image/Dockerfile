FROM python:3.12-bullseye

# Install ansible-vault & jq
RUN apt-get update && apt-get install -y gnupg software-properties-common curl jq
RUN apt update && apt -y install ansible

# Install terraform
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AA16FCBCA621E701
RUN apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main" && \
 apt-get update && apt-get install terraform=1.5.7-1 -y


# Install AWS-CLI
RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" && \
    unzip awscliv2.zip && \
    ./aws/install

# Install SOPS
RUN wget https://github.com/mozilla/sops/releases/download/v3.7.1/sops-v3.7.1.linux && \
    chmod +x sops-v3.7.1.linux && \
    mv sops-v3.7.1.linux /usr/local/bin/sops

