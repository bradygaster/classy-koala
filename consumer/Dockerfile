FROM microsoft/dotnet-nightly:3.0.100-preview-sdk as build
WORKDIR /src
COPY *.csproj .
RUN dotnet restore
COPY . .
RUN dotnet publish -o /out

FROM microsoft/dotnet-nightly:3.0-aspnetcore-runtime
WORKDIR /app
COPY --from=build /out ./
ENTRYPOINT ["dotnet", "consumer.dll"]