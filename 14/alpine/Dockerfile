FROM postgres:14-alpine AS builder

ARG PGVECTOR_VERSION=master

RUN apk add --update --no-cache \
    build-base \
    clang21 \
    git \
    llvm21

ENV PGVECTOR_VERSION=${PGVECTOR_VERSION}

RUN git clone --branch ${PGVECTOR_VERSION} https://github.com/pgvector/pgvector.git /usr/src/pgvector

WORKDIR /usr/src/pgvector

RUN make

RUN make install DESTDIR=/tmp/rootfs

FROM postgres:14-alpine

COPY --from=builder /tmp/rootfs/ /
