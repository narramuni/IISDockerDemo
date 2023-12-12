##See https://aka.ms/customizecontainer to learn how to customize your debug container and how Visual Studio uses this Dockerfile to build your images for faster debugging.
#
#FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS base
#USER app
#WORKDIR /app
#EXPOSE 8080
#EXPOSE 8081
#
#FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
#ARG BUILD_CONFIGURATION=Release
#WORKDIR /src
#COPY ["IISDockerDemo/IISDockerDemo.csproj", "IISDockerDemo/"]
#RUN dotnet restore "./IISDockerDemo/./IISDockerDemo.csproj"
#COPY . .
#WORKDIR "/src/IISDockerDemo"
#RUN dotnet build "./IISDockerDemo.csproj" -c $BUILD_CONFIGURATION -o /app/build
#
#FROM build AS publish
#ARG BUILD_CONFIGURATION=Release
#RUN dotnet publish "./IISDockerDemo.csproj" -c $BUILD_CONFIGURATION -o /app/publish /p:UseAppHost=false
#
#FROM base AS final
#WORKDIR /app
#COPY --from=publish /app/publish .
#ENTRYPOINT ["dotnet", "IISDockerDemo.dll"]


# Use the official ASP.NET runtime image as a base image
FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS base

# Set the working directory to /app
WORKDIR /app

# Expose port 80 for the application
EXPOSE 80

# Expose port 443 for HTTPS (optional, adjust according to your needs)
EXPOSE 443

# Copy the published application to the /app directory in the container
COPY --from=publish /app/publish .

# Copy the entire Models folder
COPY ["IISDockerDemo/Models", "/app/Models"]

# Set the entry point for the container
ENTRYPOINT ["dotnet", "IISDockerDemo.dll"]
