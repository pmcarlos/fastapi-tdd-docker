# pull official base image
FROM python:3.7-slim-buster

# set working directory
WORKDIR /usr/src/app

# set environment varibles
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# install system dependencies
RUN apt-get update \
  && apt-get -y install netcat gcc postgresql \
  && apt-get clean

# install python dependencies
RUN pip install pipenv
COPY Pipfile* ./
RUN pipenv install --system --deploy

# add app
COPY . .

ENTRYPOINT ["/usr/src/app/entrypoint.sh"]
