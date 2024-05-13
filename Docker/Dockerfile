FROM python:latest
# Set the working directory in the container
WORKDIR /root/workspace

# install terraform
RUN apt-get update && apt-get install -y gnupg software-properties-common

RUN wget -O- https://apt.releases.hashicorp.com/gpg | \
    gpg --dearmor | \
    tee /usr/share/keyrings/hashicorp-archive-keyring.gpg > /dev/null

RUN echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] \
    https://apt.releases.hashicorp.com $(lsb_release -cs) main" | \
    tee /etc/apt/sources.list.d/hashicorp.list

RUN apt update && apt-get install terraform

# install GCP CLI

RUN apt-get update && apt-get install apt-transport-https ca-certificates curl -y

RUN echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] \
    https://packages.cloud.google.com/apt cloud-sdk main" | \
    tee -a /etc/apt/sources.list.d/google-cloud-sdk.list && curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | \ 
    gpg --dearmor -o /usr/share/keyrings/cloud.google.gpg && apt-get update -y && apt-get install google-cloud-sdk -y

# RUN gcloud init # login stuff

# entrypoint /bin/bash
CMD ["/bin/bash"]