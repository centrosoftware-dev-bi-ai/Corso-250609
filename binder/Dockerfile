FROM jupyter/base-notebook:python-3.10

USER root

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y \
    wget \
    gnupg2 \
    ca-certificates \
    fonts-liberation \
    libnss3 \
    libxss1 \
    libasound2 \
    libatk-bridge2.0-0 \
    libgtk-3-0 \
    libx11-xcb1 \
    libxcomposite1 \
    libxcursor1 \
    libxdamage1 \
    libxrandr2 \
    libgbm1 \
    libpango1.0-0 \
    libcups2 \
    libdrm2 \
    libxinerama1 \
    libxext6 \
    libatk1.0-0 \
    libpangocairo-1.0-0 \
    libatspi2.0-0 \
    libdbus-1-3 \
    libgdk-pixbuf2.0-0 \
    libnspr4 \
    unzip \
    && rm -rf /var/lib/apt/lists/*

RUN wget -q https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb -O /tmp/chrome.deb && \
    apt-get update && \
    apt-get install -y /tmp/chrome.deb && \
    rm /tmp/chrome.deb && \
    rm -rf /var/lib/apt/lists/*

COPY . /home/jovyan/work

RUN chown -R $NB_UID:$NB_GID /home/jovyan/work

USER $NB_UID

COPY requirements.txt /tmp/
RUN pip install --no-cache-dir -r /tmp/requirements.txt

CMD ["google-chrome", "--headless", "--no-sandbox", "--disable-gpu", "--remote-debugging-port=9222"]
