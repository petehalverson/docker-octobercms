FROM alpine

RUN apk add --update \
  bash \
  curl \
  git \
  jq \
  openssh \
  openssl \
  tzdata \
  && rm -rf /var/cache/apk/*

RUN mkdir ~/.ssh && echo "StrictHostKeyChecking no" > ~/.ssh/config
RUN git clone https://github.com/aspendigital/docker-octobercms.git

COPY crontab /var/spool/cron/crontabs/root
COPY docker-entrypoint.sh /entrypoint.sh

WORKDIR /docker-octobercms

ENTRYPOINT ["/entrypoint.sh"]

CMD ["crond", "-f", "-d", "8"]
