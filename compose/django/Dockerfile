FROM python:3.8-slim

RUN apt-get update && apt-get install build-essential -y

# set environment variables
# revents Python from copying pyc files to the container.
ENV PYTHONDONTWRITEBYTECODE 1
#ensures that Python output is logged to the terminal, making it possible to monitor Django logs in realtime
ENV PYTHONUNBUFFERED 1

ARG PROJ_DIR=/app

RUN mkdir -p ${PROJ_DIR}
COPY ./back ${PROJ_DIR}
WORKDIR ${PROJ_DIR}



RUN  pip3 install --upgrade pip

# RUN apt-get update \
#     && apt-get -y install libpq-dev gcc

RUN  pip install -r ./req.txt

COPY ./compose/django/entry.sh  /entry.sh
RUN chmod +x /entry.sh

ENTRYPOINT [ "/entry.sh" ]