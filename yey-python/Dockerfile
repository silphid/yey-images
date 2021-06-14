FROM silphid/yey-base

#
# python
#
RUN apt-get install -y python-pip python3-pip python3-distutils

#
# yq (python version, installed as pyq to avoid conflict with Mike Farah's yq already in yey-base)
#
RUN pip install yq --target . && \
    mv yq /usr/local/bin/pyq
