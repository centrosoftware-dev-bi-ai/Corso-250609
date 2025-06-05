FROM ubuntu:22.04

RUN apt-get update && apt-get install -y \
    wget \
    ca-certificates \
    unzip \
    libglib2.0-0 \
    libnss3 \
    libgconf-2-4 \
    libfontconfig1 \
    libxss1 \
    libappindicator3-1 \
    libasound2 \
    fonts-liberation \
    xdg-utils \
    && rm -rf /var/lib/apt/lists/*

RUN wget -q https://deb.debian.org/debian/pool/main/c/chromium/chromium_114.0.5735.90-1~deb11u1_amd64.deb -O chromium.deb && \
    apt-get update && \
    apt-get install -y ./chromium.deb && \
    rm chromium.deb && \
    rm -rf /var/lib/apt/lists/*
