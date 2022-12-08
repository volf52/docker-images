FROM python:3.10-slim as base

ARG VERSION

RUN python3 -m pip install --no-cache-dir --user pipx==${VERSION} && python3 -m pipx ensurepath
