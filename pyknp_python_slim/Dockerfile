FROM debian as builder
ENV JUMAN_VERSION 2.0.0-rc3
ENV JUMAN_DIR jumanpp-${JUMAN_VERSION}
ENV JUMAN_URL https://github.com/ku-nlp/jumanpp/releases/download/v${JUMAN_VERSION}/jumanpp-${JUMAN_VERSION}.tar.xz
ENV KNP_VERSION 4.20
ENV KNP_DIR knp-${KNP_VERSION}
ENV KNP_URL http://nlp.ist.i.kyoto-u.ac.jp/nl-resource/knp/${KNP_DIR}.tar.bz2
RUN apt update && \
    apt -y upgrade && \
    apt install -y --no-install-recommends \
    gcc \
    g++ \
    make \
    cmake \
    xz-utils \
    bzip2 \
    libz-dev \
    wget && \
    echo "${JUMAN_URL}" && \
    wget -q --no-check-certificate ${JUMAN_URL} -O ${JUMAN_DIR}.tar.xz && \
    tar -Jxvf ${JUMAN_DIR}.tar.xz && \
    rm ${JUMAN_DIR}.tar.xz && \
    cd ${JUMAN_DIR} && \
    mkdir bld && \
    cd bld && \
    cmake .. \
    -DCMAKE_BUILD_TYPE=Release && \
    make install -j 4 && \
    cd ../.. && \
    echo "jumanpp install done" && \
    echo "${KNP_URL}" && \
    wget -q --no-check-certificate ${KNP_URL} -O ${KNP_DIR}.tar.bz2 && \
    tar jxvf ${KNP_DIR}.tar.bz2 && \
    rm ${KNP_DIR}.tar.bz2 && \
    cd ${KNP_DIR} && \
    ./configure && \
    make && \
    make install && \
    echo "KNP install done"

FROM python:3.6-slim as runner
COPY --from=builder /usr/local /usr/local
RUN pip install --upgrade pip && \
    pip install pyknp tqdm
