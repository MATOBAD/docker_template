FROM ubuntu:18.04
ENV CRF_URL https://drive.google.com/uc?export=download&id=0B4y35FiV1wh7QVR6VXJ5dWExSTQ
ENV CRF_VERSION CRF++-0.58
ENV CABOCHA_FILE_ID 0B4y35FiV1wh7SDd1Q1dUQkZQaUU
ENV CABOCHA_VERSION cabocha-0.69
ENV SYNCHA_URL https://drive.google.com/uc?export=download&id=0B4wOZ_esMVcMazQ0eGdtMnBCaWs
ENV SYNCHA_VERSION syncha-0.3.1.1
RUN apt update && \
    apt -y upgrade && \
    apt install -y --no-install-recommends \
    mecab \
    libmecab-dev \
    mecab-ipadic-utf8 \
    wget \
    gcc \
    g++ \
    make \
    curl \
    ca-certificates \
    perl \
    lp-solve && \
    wget -q --no-check-certificate ${CRF_URL} -O ${CRF_VERSION}.tar.gz && \
    tar zxfv ${CRF_VERSION}.tar.gz && \
    cd ${CRF_VERSION} && \
    ./configure && \
    make && \
    make install && \
    cd .. && \
    echo "CRF install done" && \
    curl -c /tmp/cookie "https://drive.google.com/uc?export=download&id=${CABOCHA_FILE_ID}" > /dev/null && \
    CODE="$(awk '/_warning_/ {print $NF}' /tmp/cookie)" && \
    curl -Lb /tmp/cookie "https://drive.google.com/uc?export=download&confirm=${CODE}&id=${CABOCHA_FILE_ID}" -o ${CABOCHA_VERSION}.tar.bz2 && \
    tar -jxf ${CABOCHA_VERSION}.tar.bz2 && \
    cd ${CABOCHA_VERSION} && \
    echo "/usr/local/lib" >> /etc/ld.so.conf.d/lib.conf && \
    ldconfig && \
    ./configure --with-charset=utf-8 && \
    make && \
    make install && \
    cd .. && \
    rm ${CABOCHA_VERSION}.tar.bz2 && \
    echo "cabocha install done" && \
    wget -O syncha.tar.gz 'https://drive.google.com/uc?export=download&id=0B4wOZ_esMVcMazQ0eGdtMnBCaWs' && \
    tar xzf syncha.tar.gz && \
    ldconfig