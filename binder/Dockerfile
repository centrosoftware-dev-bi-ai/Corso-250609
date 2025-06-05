FROM jupyter/base-notebook:python-3.10

USER root

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        chromium-browser \
        unzip \
        wget && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN CHROME_VER=$(chromium-browser --version | grep -oP '\d+\.\d+\.\d+') && \
    CHROMEDRIVER_VER=$(wget -qO- https://chromedriver.storage.googleapis.com/LATEST_RELEASE_${CHROME_VER}) && \
    wget -q "https://chromedriver.storage.googleapis.com/${CHROMEDRIVER_VER}/chromedriver_linux64.zip" && \
    unzip chromedriver_linux64.zip -d /usr/local/bin && \
    chmod +x /usr/local/bin/chromedriver && \
    rm chromedriver_linux64.zip

USER $NB_UID

COPY requirements.txt /tmp/
RUN pip install --no-cache-dir -r /tmp/requirements.txt
