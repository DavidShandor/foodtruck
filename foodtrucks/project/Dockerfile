FROM python:2

WORKDIR /app

COPY . .

RUN apt-get update && \
    apt-get install -y curl gnupg && \
    curl -sL https://deb.nodesource.com/setup_14.x | bash - && \
    apt-get install -y nodejs && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

WORKDIR /app/flask-app

RUN npm install

RUN npm run build

RUN pip install -r requirements.txt

ENTRYPOINT [ "python", "app.py" ]