FROM ubuntu:18.04

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y -q \
	python-all \
	python-pip

WORKDIR /opt/webapp
COPY app.py /opt/webapp
COPY Procfile /opt/webapp
COPY requirements.txt /opt/webapp
COPY tests.py /opt/webapp

RUN pip install -qr /opt/webapp/requirements.txt

EXPOSE 5000
CMD ["python", "app.py"]
