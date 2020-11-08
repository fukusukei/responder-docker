FROM python:3.8.6-alpine3.12

ENV USERNAME=fw
ARG GROUPNAME=fw
ARG USERID=1000
ARG GROUPID=1000

RUN apk update \
    && apk upgrade \
    && apk add --no-cache postgresql-dev gcc musl-dev make bash sudo \
    && pip install responder==2.0.5 SQLAlchemy==1.3.20 psycopg2 \
    && rm -rf /var/cache/apk/* \
    && adduser --disabled-password -u ${USERID} -g ${GROUPID} ${USERNAME} ${GROUPNAME} \
    && adduser ${USERNAME} wheel \
    && sed -e 's;^# \(%wheel.*NOPASSWD.*\);\1;g' -i /etc/sudoers

WORKDIR /home/${USERNAME}

USER ${USERNAME}

