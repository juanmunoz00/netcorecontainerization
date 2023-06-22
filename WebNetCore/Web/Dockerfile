FROM mcr.microsoft.com/dotnet/sdk:6.0 as build-env
WORKDIR /src

COPY . .
WORKDIR /src/Web
RUN dotnet restore

RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/aspnet:6.0
WORKDIR /app
COPY --from=build-env /src/Web/out ./
ENTRYPOINT ["dotnet", "Web.dll"]