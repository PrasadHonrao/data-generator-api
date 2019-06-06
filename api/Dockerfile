# Build Stage
FROM mcr.microsoft.com/dotnet/core/sdk:2.2-nanoserver-sac2016 AS build-env

#Restore
WORKDIR /api

COPY . .

RUN dotnet restore

#publish
RUN dotnet publish -o /publish

#runtime
FROM mcr.microsoft.com/dotnet/core/runtime:2.2-nanoserver-sac2016
WORKDIR /publish
COPY --from=build-env /publish .
ENTRYPOINT ["dotnet","api.dll"]