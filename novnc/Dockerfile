FROM alpine:latest

ENV HOME=/root \
    LANG=en_US.UTF-8 \
    LANGUAGE=en_US.UTF-8 \
    LC_ALL=C.UTF-8

RUN apk --update --upgrade add \
    bash \
    python2 \
    py-numpy \
    git

# Clone noVNC from github
RUN git clone https://github.com/kanaka/noVNC.git /root/noVNC \
    && git clone https://github.com/kanaka/websockify /root/noVNC/utils/websockify \
    && rm -rf /root/noVNC/.git \
    && rm -rf /root/noVNC/utils/websockify/.git \
    && apk del git

# Modify the launch script 'ps -p'
RUN sed -i -- "s/ps -p/ps -o pid | grep/g" /root/noVNC/utils/launch.sh

# EXPOSE 8080

# /root/noVNC/utils/launch.sh --vnc localhost:5900 --listen 8080
ENTRYPOINT ["/root/noVNC/utils/launch.sh"]
