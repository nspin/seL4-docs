# Copyright 2020 Data61, CSIRO
# SPDX-License-Identifier: BSD-2-Clause

FROM ruby:3.3

RUN apt-get update -q \
    && apt-get install -y --no-install-recommends \
        doxygen \
        python3-dev \
        python3-bs4 \
        python3-lxml \
        python3-six \
        python3-jinja2 \
        python3-sh \
        python3-pip \
        python3-pyelftools \
        npm \
    && apt-get clean autoclean \
    && apt-get autoremove --yes \
    && pip3 install --break-system-packages setuptools camkes-deps \
    && rm -rf /var/lib/{apt,dpkg,cache,log}/

# Init bundle dependencies
RUN git clone https://github.com/lsf37/docs.git -b new-design \
    && cd docs \
    && bundle install \
    && npm install \
    && cd / \
    && rm -rf docs

# Jekyll will be serving on 127.0.0.1:4000
EXPOSE 4000
