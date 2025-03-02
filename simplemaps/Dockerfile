#
# gps/simplemaps/Dockerfile
#
#   Create a PostgeSQL Docker restore container image to import SimpleMaps data.
#
#   docker build -f Dockerfile  \
#       --build-arg BASE_IMAGE="raymondstrose/postgres" \
#       --build-arg BASE_IMAGE_TAG="17" \
#       -t home/postgres-simplemaps-import:17 .
#

ARG	BASE_IMAGE="raymondstrose/postgres"
ARG	BASE_IMAGE_TAG="17"
ARG	POSTGRES_HTTP_PORT="8080"
ARG	POSTGRES_EXTERNAL_HTTP_PORT="8080"

FROM $BASE_IMAGE:$BASE_IMAGE_TAG
LABEL MAINTAINER=raymondstrose@hotmail.com

ARG	POSTGRES_HTTP_PORT

COPY simplemaps-import /usr/bin/
RUN apt-get upgrade -y; apt-get update
RUN apt-get install -y unzip
#RUN apt-get install -y inetutils-ping nmap dnsutils

WORKDIR /home/import
EXPOSE ${POSTGRES_HTTP_PORT}

ENTRYPOINT ["/usr/bin/simplemaps-import", "--debug", "--verbose"]
