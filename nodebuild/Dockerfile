FROM node:latest

WORKDIR /build

npm install --global gulp-cli

COPY build /build/
RUN chmod +x /build/build
CMD /build/build