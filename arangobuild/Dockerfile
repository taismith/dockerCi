FROM arangodb:latest

RUN apt-get update && apt-get install zip -y

WORKDIR /build
COPY build /build/ 
RUN chmod +x /build/build

CMD /build/build