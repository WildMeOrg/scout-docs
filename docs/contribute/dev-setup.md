# Dev Environment Setup
Pre-reqs and system setup are covered in [server setup](../system-administrators/server-system-setup.md). You will then need to [fork and clone the repo](pr-workflow.md).

## Local Testing

The following instructions are for once you've made changes to your local forked repo and you're ready to test.
1. `cd` to root folder of scout
1. Build the docker image of your altered code. You'll want to tag the image for easy reference later. For this demo, we use the tag `yourimage`.
    ```
    docker build -t yourimage
    ```
1. Verify you have a successful build. Check your terminal logs for the following:
    ```
    Successfully built [IMAGE-ID]
    Successfully tagged yourimage:latest
    ```
1. Run a container with your newly built docker image.
    ```
    docker run --privileged -p 1337:1337 --rm -it --gpus all --mount type=bind,source=/data,target=/data -e ENV_IP="`ip route get 1 | sed 's/^.*src \([^ ]*\).*$/\1/;q'`" -v /data/scout/db:/data/db -v /data/scout/tmp:/tmp/scout-tmp yourimage:latest
    ```
1. Provide the image directory information you created in [server setup](../system-administrators/server-system-setup.md). This will only be necessary for your first setup.
1. Check your work! Use your browser to access `localhost:1337` and see if your changes are working as desired.
1. Continue making changes or create your [PR](pr-workflow.md).

### Alternative run commands
If you are doing development work on a feature that is not impacted by image availability or ML results, you can run without GPU support.
```
docker run --privileged -p 1337:1337 --rm -it --mount type=bind,source=/data,target=/data -e ENV_IP="`ip route get 1 | sed 's/^.*src \([^ ]*\).*$/\1/;q'`" -v /data/scout_data:/data/db -v /data/scout/tmp:/tmp/scout-tmp yourimage:latest
```
