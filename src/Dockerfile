FROM mcr.microsoft.com/dotnet/aspnet:7.0 AS base
WORKDIR /app
EXPOSE 443

COPY XcExample.Api.Sometext/bin/Debug/net5.0/publish/ app/
WORKDIR /app
ENTRYPOINT ["dotnet" "XcExample.Api.Sometext.dll"]
ENV COMPlus_EnableDiagnostics=0
ENV DOTNET_EnableDiagnostics=0
ENV ASPNETCORE_ENVIRONMENT="Development"