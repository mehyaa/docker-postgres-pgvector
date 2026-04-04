FROM postgres:16-bookworm AS builder

ARG PGVECTOR_VERSION=master

RUN apt update && \
    apt install -y --no-install-recommends \
    build-essential \
    ca-certificates \
    git \
    postgresql-server-dev-16

ENV PGVECTOR_VERSION=${PGVECTOR_VERSION}

RUN git clone --branch ${PGVECTOR_VERSION} https://github.com/pgvector/pgvector.git /usr/src/pgvector

WORKDIR /usr/src/pgvector

RUN make

RUN make install DESTDIR=/tmp/rootfs

FROM postgres:16-bookworm

COPY --from=builder /tmp/rootfs/ /
