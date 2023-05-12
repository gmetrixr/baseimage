FROM postgres:14.6

RUN apt-get update && \
    apt-get install -y git make gcc && \
    rm -rf /var/lib/apt/lists/*

ENV PG_CONFIG /usr/lib/postgresql/14/bin/pg_config
RUN export PG_CONFIG && \
    git clone --branch v0.4.1 https://github.com/pgvector/pgvector.git && \
    cd pgvector && \
    make && \
    make install

RUN rm -rf /tmp/pgvector

CMD ["postgres"]