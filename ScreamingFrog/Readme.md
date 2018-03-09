# Screaming Frog SEO Spider Tool

## Build the image
```console
$ docker build -t seofrog .
```

## Create the container and mount DISPLAY
### (Optional:  --memory=4g )
```console
$ docker create --memory=4g -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=unix$DISPLAY --name seo_frog seofrog
```
## Create the container with local mount to use save/load functions
```console
$ docker create --memory=4g -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=unix$DISPLAY -v /path_to/local_dir/:/home/developer --name seo_frog seofrog
```

## Run the container
```console
$ docker start seo_frog
```

### After running the container, activate the software using your licence, close it and run again 
```console
$ docker start seo_frog
````