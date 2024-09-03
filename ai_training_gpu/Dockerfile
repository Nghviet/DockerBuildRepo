FROM nvidia/cuda:12.6.0-cudnn-devel-ubuntu20.04
RUN ln -snf /usr/share/zoneinfo/$CONTAINER_TIMEZONE /etc/localtime && echo $CONTAINER_TIMEZONE > /etc/timezone
RUN apt-get update && apt-get install -y curl \
    build-essential \
    bash-completion \
    git \ 
    --no-install-recommends \
    ca-certificates \
    python3.9 python3.9-distutils \
    && \
    apt-get clean
RUN curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py && python3.9 get-pip.py

RUN useradd -m vietnh
RUN chown -R vietnh:vietnh /home/vietnh/
COPY --chown=vietnh . /home/vietnh/workspace/

USER vietnh
RUN cd /home/vietnh/workspace/ && pip3 install -r requirement.txt
WORKDIR /home/vietnh/workspace