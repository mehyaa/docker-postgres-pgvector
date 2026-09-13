FROM postgres:15-alpine AS builder

RUN apk add --update --no-cache \
    build-base \
    clang21 \
    llvm21

COPY --from=pgvector-src / /usr/src/pgvector

WORKDIR /usr/src/pgvector

RUN make

RUN make install DESTDIR=/tmp/rootfs

FROM postgres:15-alpine

COPY --from=builder /tmp/rootfs/ /
