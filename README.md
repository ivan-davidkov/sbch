# sbch
chromium-browser in a docker container build on apline:edge

This is the Git repo of my [sbcb](https://hub.docker.com/r/idavidkov/chromium-browser/). See [the Docker Hub page](https://hub.docker.com/r/idavidkov/) for the full readme on how to use this Docker image and for information regarding contributing and issues.

# Starting a chromium-browser instance is simple:

start chromium-browser with video support only
```sh
docker run --rm -it -e DISPLAY -v /tmp/.X11-unix/:/tmp/.X11-unix idavidkov/chromium-browser
```
... where --rm will remove the container after you close the last window, -e DISPLAY will export your DISPLAY inside the container, -v /tmp/.X11-unix/:/tmp/.X11-unix will expose your running X server socket inside the container.

start chromium-browser with display and sound on the host
```sh
docker run --rm -it -e DISPLAY -v /tmp/.X11-unix/:/tmp/.X11-unix -v /dev/snd:/dev/snd --privileged idavidkov/chromium-browser
```
... where --rm will remove the container after you close the last window, -e DISPLAY will export your DISPLAY inside the container, -v /tmp/.X11-unix/:/tmp/.X11-unix will expose your running socket inside the container, -v /dev/snd:/dev/snd will connect your running sound system to the container /!\ but you also need to use --privileged option in order to get the sound running.
