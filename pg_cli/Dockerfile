FROM volf52/pipx:1.1.0 as base

ARG PGCLI_VERSION

RUN apt-get update && apt-get upgrade -y && apt-get install libpq-dev -y && rm -rf /var/lib/apt/lists/* && /root/.local/bin/pipx install pgcli==${PGCLI_VERSION} --pip-args="--no-cache-dir"

CMD [ "pgcli", "--help" ]
