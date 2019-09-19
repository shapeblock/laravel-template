This repo contains the following artifacts required to run Laravel apps on OpenShift.

1. PHP FPM image running PHP 7.2
2. Nginx image
3. Laravel template

# How to use

## Build the s2i image

```
$ cd s2i-build

$ docker build -t shapeblock/laravel:7.2 .

$ docker push shapeblock/laravel:7.2

$ oc import-image shapeblock/laravel:7.2 --confirm

# or if creating a new tag

$ oc  tag --source=docker shapeblock/laravel:7.2 shapeblock/laravel:7.2 

```

## Build the nginx image

```
$ docker build -t shapeblock/nginx-laravel:1.17 .

$ docker push shapeblock/nginx-laravel:1.17

$ oc import-image shapeblock/nginx-laravel:1.17 --confirm

```

## Upload the template

The template is a quick and UI-friendly way to boot a Laravel application using the above artifacts. This can be imported into the project by running,

```
$ oc apply -f laravel-template.yml
```

**NOTE** you have to change the project name in the template according to where you have imported the base images.

