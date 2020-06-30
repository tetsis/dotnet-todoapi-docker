# Dotnet todoapi docker
## Download
```
git clone https://github.com/tetsis/dotnet-todoapi-docker.git
cd dotnet-todoapi-docker
```

## Migration
```
docker-compose -f docker-compose-db.yml up -d
cd todoapi/todoapi
dotnet ef migrations add InitialCreate
dotnet ef database update
cd ../..
docker-compose -f docker-compose-db.yml down
```

### Reference
https://docs.microsoft.com/ja-jp/ef/core/managing-schemas/migrations/?tabs=dotnet-core-cli

## Run
```
docker-compose up -d
```

## Confirm
### GET
```
curl http://localhost:5000/WeatherForecast
curl http://localhost:5000/api/TodoItems
```

### POST ([Windows curl](https://curl.haxx.se/))
```
curl.exe -X POST -H "Content-Type:application/json" -d "{\"name\":\"walk dog\",\"isComplete\":true}" http://localhost:5000/api/TodoItems
```