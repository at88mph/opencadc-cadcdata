FROM python:3.9-slim AS build

RUN apt-get update \
    && apt-get install -y gcc make libssl-dev

RUN pip --no-cache-dir install cadcdata

FROM python:3.9-slim AS lib

RUN apt update \
    && apt install -y libmagic-dev

FROM python:3.9-slim

COPY --from=lib /usr/ /usr/
COPY --from=lib /etc/ /etc/
COPY --from=build /usr/local/ /usr/local/

CMD ["cadcget"]
