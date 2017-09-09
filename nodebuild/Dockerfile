FROM node:latest

WORKDIR /build

RUN npm install --global gulp-cli

COPY build /build/
RUN chmod +x /build/build
CMD /build/build