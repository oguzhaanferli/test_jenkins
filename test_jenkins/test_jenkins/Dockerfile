FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /src
COPY ["test_jenkins/test_jenkins.csproj", "test_jenkins/"]
RUN dotnet restore "test_jenkins/test_jenkins.csproj"
COPY . .
WORKDIR "/src/test_jenkins"
RUN dotnet build "test_jenkins.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "test_jenkins.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "test_jenkins.dll"]
