FROM alpine:3.5

ARG CI_BUILD_URL
ARG BUILD_DATE
ARG VCS_REF
ARG VERSION

LABEL \
    io.github.jumanjiman.ci-build-url=$CI_BUILD_URL \
    io.github.jumanjiman.version=$VERSION \
    io.github.jumanjiman.build-date=$BUILD_DATE \
    io.github.jumanjiman.vcs-ref=$VCS_REF \
    io.github.jumanjiman.license="Apache License 2.0" \
    io.github.jumanjiman.docker.dockerfile="/runtime/Dockerfile" \
    io.github.jumanjiman.vcs-type="Git" \
    io.github.jumanjiman.vcs-url="https://github.com/jumanjihouse/docker-caddy.git"

RUN apk upgrade --no-cache --available && \
    apk add --no-cache \
      ca-certificates \
      git \
      libressl \
    && adduser -Du 1000 caddy

RUN echo "hello world" > /home/caddy/index.html

VOLUME ["/etc/caddy"]
VOLUME ["/home/caddy"]

COPY caddy /usr/sbin/caddy

# Run as an unprivileged user.
USER caddy
ENTRYPOINT ["/usr/sbin/caddy"]
