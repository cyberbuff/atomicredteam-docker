# atomicredteam-docker

This repo builds and pushes docker images for `invoke-atomicredteam`. Some of the use cases include:

- Users can quickly pull down this image and test the functionality of `atomic-red-team` and `invoke-atomicredteam`.
- This can also be used to run periodic tasks and download the execution logs for continuous detection and validation.

```
Note: This repo is a work in progress.
```
### Supported Platforms and Architectures:

| Platforms   |              Image Name              |
| :---------- | :----------------------------------: |
| linux/amd64 | cyberbuff/invoke-atomicredteam:amd64 |
| linux/arm64 | cyberbuff/invoke-atomicredteam:arm64 |

### Work in Progress

- windows/amd64
- windows/arm64


## How it works:

Microsoft publishes [powershell docker images](https://hub.docker.com/_/microsoft-powershell) almost for all of the platforms. We can use this to pull down a minimal base image with powershell and add the necessary requirements that's needed for `atomic-red-team`.


# Building locally

Run the following command to build and run the image locally.

```sh
platform=arm64
docker build -t cyberbuff/invoke-atomicredteam:$platform $platform
docker run -it cyberbuff/invoke-atomicredteam:$platform
```