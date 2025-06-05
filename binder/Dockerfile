FROM jupyter/base-notebook:python-3.10

USER root

RUN apt-get update && apt-get install -y --no-install-recommends \
    chromium \
    wget \
    unzip \
    libglib2.0-0 \
    libnss3 \
    libgconf-2-4 \
    libfontconfig1 \
    libxss1 \
    libappindicator1 \
    libasound2 \
    fonts-liberation \
    xdg-utils \
    && rm -rf /var/lib/apt/lists/*

# Install specific chromedriver version manually
ENV CHROME_DRIVER_VERSION=116.0.5845.96

RUN wget -q https://chromedriver.storage.googleapis.com/${CHROME_DRIVER_VERSION}/chromedriver_linux64.zip && \
    unzip chromedriver_linux64.zip && \
    mv chromedriver /usr/local/bin/chromedriver && \
    chmod +x /usr/local/bin/chromedriver && \
    rm chromedriver_linux64.zip

USER $NB_UID

COPY requirements.txt /tmp/
RUN pip install --no-cache-dir -r /tmp/requirements.txt
