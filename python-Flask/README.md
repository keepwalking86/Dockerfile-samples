## Build image

`docker build -t hub.example.com/python:1.0.0 .`

## Run container

`docker run --name application -d -p 5000:5000 hub.example.com/python:1.0.0`
