#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/aspnet:5.0 AS base
WORKDIR /app
EXPOSE 80

FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR /src
COPY ["XcExample.Api.Sometext/XcExample.Api.Sometext.csproj", "XcExample.Api.Sometext/"]
RUN dotnet restore "XcExample.Api.Sometext/XcExample.Api.Sometext.csproj"
COPY . .
WORKDIR "/src/XcExample.Api.Sometext"
RUN dotnet build "XcExample.Api.Sometext.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "XcExample.Api.Sometext.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "XcExample.Api.Sometext.dll"]
ENV ASPNETCORE_ENVIRONMENT="Development"