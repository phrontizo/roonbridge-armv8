# roonbridge-armv8
Docker file for running Roon Bridge on Armbian armv8 (tested on an OrangePi Zero+ only).

This runs RoonBridge directly, bypassing the `start.sh` script. Logs and other persistent data go into `/var/roon`, which needs to be mapped to a volume or host directory. I have not tested it when RoonBridge updates yet. RoonBridge itself is not included in the image - it is downloaded and unpacked on first run.

## Running
```
docker run --detach \
           --restart always \
           --device /dev/snd \
           --net host \
           -v roon_data:/var/roon \
           --name roonbridge \
           phrontizo/roonbridge-armv8
```
Runs as UID 1000, GID 29 (audio). Needs to run as a UID:GID that has rw access to `/dev/snd` - change as appropriate for your system.
