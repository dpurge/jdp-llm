ARG PG_MAJOR=15
ARG PG_VECTOR=0.5.1

FROM postgres:${PG_MAJOR}

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-mark hold locales && \
    apt-get install -y --no-install-recommends \
      build-essential \
      postgresql-server-dev-${PG_MAJOR} \
      wget && \
    wget https://github.com/pgvector/pgvector/archive/v${PG_VECTOR}.tar.gz && \
    tar -xzvf v${PG_VECTOR}.tar.gz && \
    cd pgvector-${PG_VECTOR} && \
    make OPTFLAGS="" && \
    make install && \
    cd .. && \
    rm -r pgvector-0.4.4 && \
    apt-get remove -y build-essential postgresql-server-dev-${PG_MAJOR} && \
    apt-get autoremove -y && \
    apt-mark unhold locales
