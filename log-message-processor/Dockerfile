FROM p
FROM python:3.7

WORKDIR /app

COPY requirements.txt .

RUN pip install --upgrade pip && \
    pip install --no-deps py_zipkin==0.11.0 redis==2.10.6 requests && \
    pip install thriftpy2

COPY . .

CMD ["python", "main.py"]
