# Build Image Stage
FROM mcr.microsoft.com/dotnet/core/sdk:2.2-nanoserver-sac2016 AS build-env
WORKDIR /api
COPY . .
RUN dotnet restore
RUN dotnet publish -o /publish

# Runtime Image Stage
FROM mcr.microsoft.com/dotnet/core/runtime:2.2-nanoserver-sac2016
WORKDIR /publish
COPY --from=build-env /publish .
ENTRYPOINT ["dotnet","api.dll"]