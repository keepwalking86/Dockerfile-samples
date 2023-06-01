## Build image

`docker build -t hub.example.com/application:1.0.0 .`

## Run container

`docker run --name application -d -p 3000:3000 hub.example.com/application:1.0.0`
