
# Use the "mcr.microsoft.com/dotnet/sdk:5.0" image as base.
# This image contains the .NET SDK needed to BUILD the project
# and .NET runtime needed to RUN the project.
FROM mcr.microsoft.com/dotnet/sdk:5.0

# Copy all files from the current directory ON THE HOST MACHINE
# to the /src folder ON THE CONTAINER
COPY . /src
# Go to the /src directory
WORKDIR /src

# Build the project
RUN dotnet build "aspnetapp.csproj" -c Release -o /app/build

# Publish the project
RUN dotnet publish "aspnetapp.csproj" -c Release -o /app/publish

# Expose the application on port :80
ENV ASPNETCORE_URLS=http://+:80

# This command will run when the container starts.
# This will run the already build application.
ENTRYPOINT ["dotnet", "/app/publish/aspnetapp.dll"]