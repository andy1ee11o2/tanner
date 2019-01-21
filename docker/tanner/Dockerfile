FROM alpine

# Include dist
ADD dist/ /root/dist/

# Setup apt
RUN apk -U --no-cache add \
               build-base \
               git \
               libcap \
               libffi-dev \
               libressl-dev \
               linux-headers \
               py3-yarl \
               python3 \
               python3-dev && \ 

# Setup Tanner
    git clone --depth=1 https://github.com/andy1ee11o2/tanner /opt/tanner && \
    cp /root/dist/config.py /opt/tanner/tanner/ && \
    cd /opt/tanner/ && \
    pip3 install --no-cache-dir --upgrade pip setuptools && \
    pip3 install --no-cache-dir -r requirements.txt && \
    python3 setup.py install && \
    cd / && \


# Clean up
    apk del --purge \
            build-base \
            linux-headers \
            python3-dev && \
    rm -rf /root/* && \
    rm -rf /tmp/* /var/tmp/* && \
    rm -rf /var/cache/apk/*

# mkdir tanner
    mkdir /var/log/tanner /tmp/tanner && \
    touch /var/log/tanner/tanner_report.json /tmp/tanner//tanner.log /tmp/tanner//tanner.err

# Start conpot
WORKDIR /opt/tanner
CMD tanner 
