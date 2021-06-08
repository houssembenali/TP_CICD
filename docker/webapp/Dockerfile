FROM python:alpine

WORKDIR /usr/src/

COPY ./src/* app/


COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt


EXPOSE 3000

CMD [ "python", "./app/main.py" ]
