FROM postgres:15-bookworm AS builder

RUN apt update && \
    apt install -y --no-install-recommends \
    build-essential \
    ca-certificates \
    postgresql-server-dev-15

COPY --from=pgvector-src / /usr/src/pgvector

WORKDIR /usr/src/pgvector

RUN make

RUN make install DESTDIR=/tmp/rootfs

FROM postgres:15-bookworm

COPY --from=builder /tmp/rootfs/ /
