# Laravel using for PHP8.2, Apache support libraries:

- MySQL

- MongoDB

- Redis

# Optimizing builds

## Step1: Build image as base

`docker build -t keepwalking/php8.2-apache-base:latest -f Dockerfile-base .`

## Step2: Push image base to repo

`docker push keepwalking/php8.2-apache-base:latest`

## Step3: Build main image

`docker build -t hub.example.com/example/application-name:latest -f Dockerfile .`


