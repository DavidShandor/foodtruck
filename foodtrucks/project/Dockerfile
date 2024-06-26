FROM node:lts-alpine3.20 AS builder

WORKDIR /app

COPY . .

WORKDIR /app/flask-app

RUN npm install

RUN npm run build


FROM python:2-alpine3.11

WORKDIR /app/flask-app

COPY --from=builder /app/flask-app/static static

COPY --from=builder /app/flask-app/templates templates

COPY --from=builder /app/flask-app/requirements.txt .

COPY --from=builder /app/flask-app/app.py .

RUN pip install -r requirements.txt

EXPOSE 5000

ENTRYPOINT [ "python", "app.py" ]
