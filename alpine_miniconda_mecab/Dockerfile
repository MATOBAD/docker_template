FROM frolvlad/alpine-glibc
ENV PATH /opt/conda/bin:$PATH
ENV LANG C.UTF-8
ENV MINICONDA Miniconda3-latest-Linux-x86_64.sh
ENV MECAB_URL https://drive.google.com/uc?export=download&id=0B4y35FiV1wh7cENtOXlicTFaRUE
ENV MECAB_VERSION mecab-0.996
ENV MECAB_DIC_URL https://drive.google.com/uc?export=download&id=0B4y35FiV1wh7MWVlSDBCSXZMTXM
ENV MECAB_DIC_VERSION mecab-ipadic-2.7.0-20070801
RUN apk add --update --no-cache wget bash build-base make && \
    wget -q --no-check-certificate https://repo.continuum.io/miniconda/$MINICONDA && \
    bash /Miniconda3-latest-Linux-x86_64.sh -b -p /opt/conda && \
    pip install numpy gensim jaconv mecab-python3 && \
    ln -s /opt/conda/bin/* /usr/local/bin/ && \
    wget -q --no-check-certificate ${MECAB_URL} -O ${MECAB_VERSION}.tar.gz && \
    tar zxf ${MECAB_VERSION}.tar.gz && \
    cd ${MECAB_VERSION} && \
    ./configure --with-charset=utf8 && \
    make && \
    make install && \
    cd .. && \
    rm ${MECAB_VERSION}.tar.gz && \
    wget ${MECAB_DIC_URL} -O ${MECAB_DIC_VERSION}.tar.gz && \
    tar -xvf ${MECAB_DIC_VERSION}.tar.gz && \
    cd ${MECAB_DIC_VERSION} && \
    ./configure --with-charset=utf8 && \
    make && \
    make install && \
    cd .. && \
    rm ${MECAB_DIC_VERSION}.tar.gz && \
    rm -rf /root/.[acpw]* /$MINICONDA /opt/conda/pkgs/*