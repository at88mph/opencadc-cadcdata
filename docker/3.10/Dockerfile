ARG OPENCADC_PYTHON_VERSION=3.10
FROM python:${OPENCADC_PYTHON_VERSION}-slim AS build

RUN apt-get update \
    && apt-get install -y gcc make libssl-dev

RUN pip --no-cache-dir install cadcdata

FROM python:${OPENCADC_PYTHON_VERSION}-slim AS lib

RUN apt update \
    && apt install -y libmagic-dev

FROM python:${OPENCADC_PYTHON_VERSION}-slim

COPY --from=lib /usr/ /usr/
COPY --from=lib /etc/ /etc/
COPY --from=build /usr/local/ /usr/local/

CMD ["cadcget"]
