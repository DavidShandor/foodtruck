FROM python:2-alpine3.11

WORKDIR /app

COPY . .

RUN apk add --update npm

WORKDIR /app/flask-app

RUN npm install

RUN npm run build

RUN pip install -r requirements.txt

ENTRYPOINT [ "python", "app.py" ]