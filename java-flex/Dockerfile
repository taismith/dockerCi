FROM quay.io/qdotmediaorg/dotnetjava

ADD flex_sdk_3.6a.zip .

RUN apt-get update

RUN apt-get install -y unzip

RUN mkdir /flex

RUN rm -rf /var/lib/apt/lists/* && apt-get clean

RUN unzip flex_sdk_3.6a.zip -d /flex

RUN rm flex_sdk_3.6a.zip