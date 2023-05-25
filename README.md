# atomicredteam-docker

This repo builds and pushes docker images for `invoke-atomicredteam`. Some of the use cases include:

- Users can quickly pull down this image and test the functionality of `atomic-red-team` and `invoke-atomicredteam`.
- This can also be used to run periodic tasks (Kubernetes Cron Jobs/ CI-CD) and download the execution logs for continuous detection and validation.

```
Note: This repo is a work in progress.
```
### Supported Platforms and Architectures:

| Platforms   |              Image Name              |
| :---------- | :----------------------------------: |
| windows/amd64 | `docker run -it cyberbuff/invoke-atomicredteam:latest` |
| linux/amd64 | `docker run -it cyberbuff/invoke-atomicredteam:latest` |
| linux/arm64 | `docker run -it cyberbuff/invoke-atomicredteam:arm64` |

```
Note: linux/arm64 tested on M1 Macbook Air, windows/amd64 and linux/amd64 are tested on a Windows 11 machine. If you have any issues running on your machine, feel free to create a Github Issue.
```

## How it works:

Microsoft publishes [powershell docker images](https://hub.docker.com/_/microsoft-powershell) almost for all of the platforms. We can use this to pull down a minimal base image with powershell and add the necessary requirements that's needed for `atomic-red-team`.


## Pre-Reqs
Check [Windows PreReqs](https://learn.microsoft.com/en-us/virtualization/windowscontainers/quick-start/set-up-environment?tabs=dockerce) here.

## Building locally

Run the following command to build and run the image locally.

```sh
docker build -t cyberbuff/invoke-atomicredteam:latest .
docker run -it cyberbuff/invoke-atomicredteam:latest
```
