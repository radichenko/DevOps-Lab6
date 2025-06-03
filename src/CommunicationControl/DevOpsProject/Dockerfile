FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src

COPY . .

RUN dotnet restore src/CommunicationControl/DevOpsProject.sln
RUN dotnet publish src/CommunicationControl/DevOpsProject/DevOpsProject.CommunicationControl.API.csproj -c Release -o /app/publish

FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS runtime
WORKDIR /app
COPY --from=build /app/publish .
ENV ASPNETCORE_URLS=http://+:8000
EXPOSE 8000
ENTRYPOINT ["dotnet", "DevOpsProject.CommunicationControl.API.dll"]