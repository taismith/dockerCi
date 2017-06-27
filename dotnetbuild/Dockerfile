FROM microsoft/dotnet:1.1.1-sdk

ENV WORKSPACE_NAME blank
ENV DOTNET_SKIP_FIRST_TIME_EXPERIENCE true
ENV NUGET_XMLDOC_MODE skip
ENV DOTNET_CLI_TELEMETRY_OPTOUT 1

WORKDIR /build
COPY build /build/ 
RUN chmod +x /build/build

CMD /build/build
