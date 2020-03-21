FROM ubuntu:18.04
RUN apt-get update && \
    apt-get upgrade && \
    apt-get install -y --no-install-recommends mecab libmecab-dev mecab-jumandic-utf8 wget && \
    wget --no-check-certificate https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O /tmp/miniconda.sh && \
    bash /tmp/miniconda.sh -bfp /usr/local && \
    rm -rf /tmp/miniconda.sh && \
    pip install mecab-python3 && \
    conda update conda && \
    apt remove -y --purge wget && \
    apt -y clean && \
    rm -rf /var/lib/apt/lists/* /var/log/dpkg.log