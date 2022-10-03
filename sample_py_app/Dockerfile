FROM ubuntu:18.04

ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=Europe/Moscow

RUN apt-get update && apt-get install -y -q \
	python-all \
	python-pip

ADD ./app.py /opt/webapp
ADD ./Procfile /opt/webapp
ADD ./requirements.txt /opt/webapp
ADD ./tests.py /opt/webapp

RUN pip install -qr /opt/webapp/requirements.txt

EXPOSE 5000
CMD ["python", "/opt/webapp/app.py"]
