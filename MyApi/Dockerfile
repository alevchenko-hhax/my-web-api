FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build-env
WORKDIR /app

COPY *.csproj ./
RUN dotnet restore


COPY . ./
RUN dotnet publish -c Release -o out

# Set the final image
FROM mcr.microsoft.com/dotnet/aspnet:7.0
WORKDIR /app
COPY --from=build-env /app/out .


EXPOSE 80

# Start the application
ENTRYPOINT ["dotnet", "MyApi.dll"]