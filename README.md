# Firefox

## Build
Via GitHub repository
```bash
$ docker build --tag alireaza/firefox:$(date -u +%Y%m%d) --tag alireaza/firefox:latest https://github.com/alireaza/firefox.git
```

## Run
```bash
$ docker run \
--interactive \
--tty \
--rm \
--mount="type=bind,source=/tmp/.X11-unix,target=/tmp/.X11-unix" \
--env="DISPLAY=$DISPLAY" \
--device="/dev/dri:/dev/dri" \
--env="PULSE_SERVER=unix:${XDG_RUNTIME_DIR}/pulse/native" \
--mount="type=bind,source=${XDG_RUNTIME_DIR}/pulse/native,target=${XDG_RUNTIME_DIR}/pulse/native" \
--env="TZ=$(cat /etc/timezone)" \
--cap-add=SYS_ADMIN \
--ipc host \
--mount="type=bind,source=/dev/shm,target=/dev/shm" \
--mount="type=bind,source=$(pwd)/udocker,target=/home/udocker" \
--name="firefox" \
alireaza/firefox
```

