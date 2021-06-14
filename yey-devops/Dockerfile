FROM silphid/yey-base

#
# kubectl
#
# cli to manage kubernetes clusters
# https://kubernetes.io/docs/reference/kubectl/kubectl/
#
RUN curl -fsLO https://storage.googleapis.com/kubernetes-release/release/v1.21.1/bin/linux/amd64/kubectl && \
    chmod +x kubectl && \
    mv kubectl /usr/local/bin/kubectl

#
# helm 3
#
# the package manager for kubernetes
# https://helm.sh/
#
ARG HELM_VERSION=3.6.0
RUN curl -fsL https://get.helm.sh/helm-v$HELM_VERSION-linux-amd64.tar.gz \
    | tar xzv -C /usr/local/bin --strip=1 linux-amd64/helm

#
# helm-diff
#
# helm plugin showing diff preview of what a helm upgrade would change
# https://github.com/databus23/helm-diff
#
RUN helm plugin install https://github.com/databus23/helm-diff --version master

#
# helmfile
#
# cli and declarative spec for deploying helm charts
# https://github.com/roboll/helmfile
#
ARG HELMFILE_VERSION=0.139.9
RUN curl -fsL --output /usr/local/bin/helmfile https://github.com/roboll/helmfile/releases/download/v$HELMFILE_VERSION/helmfile_linux_amd64 && \
    chmod +x /usr/local/bin/helmfile

#
# k9s
#
# cli to manage kubernetes clusters in style!
#
# https://k9scli.io/
#
ARG K9S_VERSION=0.24.10
RUN curl -fsL https://github.com/derailed/k9s/releases/download/v$K9S_VERSION/k9s_v${K9S_VERSION}_Linux_x86_64.tar.gz \
    | tar xzv -C /usr/local/bin k9s

#
# ksd
#
# kubernetes secret decoder to visualize secrets in plain text
#
# https://github.com/mfuentesg/ksd
#
ARG KSD_VERSION=1.0.6
RUN curl -fsL https://github.com/mfuentesg/ksd/releases/download/v$KSD_VERSION/ksd_${KSD_VERSION}_Linux_x86_64.tar.gz \
    | tar xzv -C /usr/local/bin ksd

#
# kail
#
# kubernetes tail, for viewing log tails
#
# https://github.com/boz/kail
#
RUN bash <( curl -sfL https://raw.githubusercontent.com/boz/kail/master/godownloader.sh) -b "$GOPATH/bin"

#
# terraform
#
# cli to manage cloud infrastructure via terraform
#
# https://www.terraform.io/docs/cli/index.html
#
ARG TERRAFORM_VERSION=1.0.0
RUN TMP=$(mktemp) && \
    curl -fsL --output $TMP https://releases.hashicorp.com/terraform/$TERRAFORM_VERSION/terraform_${TERRAFORM_VERSION}_linux_amd64.zip && \
    unzip -p $TMP terraform > /usr/local/bin/terraform && \
    chmod +x /usr/local/bin/terraform && \
    rm $TMP && \
    terraform -install-autocomplete

COPY files/ /
