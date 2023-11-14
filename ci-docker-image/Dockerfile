FROM python:3.12-bullseye

# Install ansible-vault
RUN apt-get update && apt-get install -y gnupg software-properties-common curl
RUN apt update && apt -y install ansible

# Install terraform
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AA16FCBCA621E701
RUN apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main" && \
 apt-get update && apt-get install terraform=1.3.7


# Install AWS-CLI
RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" && \
    unzip awscliv2.zip && \
    ./aws/install