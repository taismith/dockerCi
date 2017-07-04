FROM microsoft/dotnet:1.1.1-sdk
WORKDIR /build
#Add Jenkins user to dotnet container
RUN echo jenkins:x:1000:1000::/var/jenkins_home:/bin/bash >> /etc/passwd
RUN mkdir /var/jenkins_home
RUN chown jenkins /var/jenkins_home 
VOLUME ["/var/jenkins_home"]
ENV WORKSPACE_NAME blank
ENV DOTNET_SKIP_FIRST_TIME_EXPERIENCE true
ENV NUGET_XMLDOC_MODE skip
ENV DOTNET_CLI_TELEMETRY_OPTOUT 1
COPY build /build/ 
RUN chmod +x /build/build
USER jenkins
CMD /build/build