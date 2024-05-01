#See https://aka.ms/customizecontainer to learn how to customize your debug container and how Visual Studio uses this Dockerfile to build your images for faster debugging.

#Para funcionar necesita tener la compatibilidad con ddocker y visual studio.
#En caso no contar con ella:
#Ir a herramientas -> Adminstrador de paquetes NuGuet-> Consola de paquetes -> Ejecute el siguiente comando.
# NuGet\Install-Package Microsoft.VisualStudio.Azure.Containers.Tools.Targets -Version 1.20.1
FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS base
USER app
WORKDIR /app
EXPOSE 8080
EXPOSE 8081

FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
ARG BUILD_CONFIGURATION=Release
WORKDIR /src
COPY ["WebAPINET8/WebAPINET8.csproj", "WebAPINET8/"]
RUN dotnet restore "./WebAPINET8/WebAPINET8.csproj"
COPY . .
WORKDIR "/src/WebAPINET8"
RUN dotnet build "./WebAPINET8.csproj" -c $BUILD_CONFIGURATION -o /app/build

FROM build AS publish
ARG BUILD_CONFIGURATION=Release
RUN dotnet publish "./WebAPINET8.csproj" -c $BUILD_CONFIGURATION -o /app/publish /p:UseAppHost=false

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebAPINET8.dll"]