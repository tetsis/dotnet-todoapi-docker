FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /app

# copy csproj and restore as distinct layers
COPY *.sln .
COPY todoapi/*.csproj ./todoapi/
RUN dotnet restore

# copy everything else and build app
COPY todoapi/. ./todoapi/
WORKDIR /app/todoapi
RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS runtime
WORKDIR /app
COPY --from=build /app/todoapi/out ./
ENTRYPOINT ["dotnet", "todoapi.dll"]