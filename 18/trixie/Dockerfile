FROM postgres:18-trixie AS builder

RUN apt update && \
    apt install -y --no-install-recommends \
    build-essential \
    ca-certificates \
    postgresql-server-dev-18

COPY --from=pgvector-src / /usr/src/pgvector

WORKDIR /usr/src/pgvector

RUN make

RUN make install DESTDIR=/tmp/rootfs

FROM postgres:18-trixie

COPY --from=builder /tmp/rootfs/ /
