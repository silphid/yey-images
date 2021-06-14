FROM silphid/yey-devops

#
# aws
#
# cli to manage AWS services
# https://aws.amazon.com/cli
#
ARG AWS_CLI_VERSION=2.2.11
RUN TMP=$(mktemp -d) && \
    cd $TMP && \
    curl -fsL -o "awscliv2.zip" "https://awscli.amazonaws.com/awscli-exe-linux-x86_64-$AWS_CLI_VERSION.zip" && \
    unzip awscliv2.zip && \
    ./aws/install && \
    rm -rf $TMP

#
# eksctl
#
# cli to manage kubernetes clusters on EKS
# https://eksctl.io/
#
RUN curl -fsL "https://github.com/weaveworks/eksctl/releases/download/latest_release/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp && \
    mv /tmp/eksctl /usr/local/bin

COPY files/ /
