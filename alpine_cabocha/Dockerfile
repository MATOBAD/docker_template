FROM frolvlad/alpine-glibc
ENV LANG C.UTF-8
ENV MECAB_URL https://drive.google.com/uc?export=download&id=0B4y35FiV1wh7cENtOXlicTFaRUE
ENV MECAB_VERSION mecab-0.996
ENV MECAB_DIC_URL https://drive.google.com/uc?export=download&id=0B4y35FiV1wh7MWVlSDBCSXZMTXM
ENV MECAB_DIC_VERSION mecab-ipadic-2.7.0-20070801
ENV CRF_URL https://drive.google.com/uc?export=download&id=0B4y35FiV1wh7QVR6VXJ5dWExSTQ
ENV CRF_VERSION CRF++-0.58
ENV CABOCHA_FILE_ID 0B4y35FiV1wh7SDd1Q1dUQkZQaUU
ENV CABOCHA_VERSION cabocha-0.69
RUN apk add --update --no-cache wget bash build-base make gcc g++ curl && \
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
    wget -q --no-check-certificate ${CRF_URL} -O ${CRF_VERSION}.tar.gz && \
    tar zxfv ${CRF_VERSION}.tar.gz && \
    cd ${CRF_VERSION} && \
    ./configure && \
    make && \
    make install && \
    cd .. && \
    rm ${CRF_VERSION}.tar.gz && \
    curl -sc /tmp/cookie "https://drive.google.com/uc?export=download&id=${CABOCHA_FILE_ID}" > /dev/null && \
    CODE="$(awk '/_warning_/ {print $NF}' /tmp/cookie)" && \
    curl -Lb /tmp/cookie "https://drive.google.com/uc?export=download&confirm=${CODE}&id=${CABOCHA_FILE_ID}" -o ${CABOCHA_VERSION}.tar.bz2 && \
    tar -jxf ${CABOCHA_VERSION}.tar.bz2 && \
    cd ${CABOCHA_VERSION} && \
    ./configure --with-charset=utf-8 && \
    make && \
    make install && \
    cd .. && \
    rm ${CABOCHA_VERSION}.tar.bz2 && \
    rm -rf /root/.[acpw]*