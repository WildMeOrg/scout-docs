# Dev Environment Setup
Pre-reqs and system setup are covered in [server setup](../setup-and-maintenance/server-system-setup.md). You will then need to [fork and clone the repo](pr-workflow.md).

## Local Testing

The following instructions are for once you've made changes to your local forked repo and you're ready to test.
1. `cd` to root folder of scout
1. Build the docker image of your altered code. You'll want to tag the image for easy reference later. For this demo, we use the tag `yourimage`.
    ```
    docker build -t yourimage .
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
1. Provide the image directory information you created in [server setup](../setup-and-maintenance/server-system-setup.md). This will only be necessary for your first setup.
1. Check your work! Use your browser to access `localhost:1337` and see if your changes are working as desired.
1. Continue making changes or create your [PR](pr-workflow.md).

### Run without GPU
If you are doing development work on a feature that is not impacted by image availability or ML results, you can go from [storage setup](../setup-and-maintenance//server-system-setup.md#storage) to setting up your code repo.
```
docker run --privileged -p 1337:1337 --rm -it --mount type=bind,source=/data,target=/data -e ENV_IP="`ip route get 1 | sed 's/^.*src \([^ ]*\).*$/\1/;q'`" -v /data/scout_data:/data/db -v /data/scout/tmp:/tmp/scout-tmp yourimage:latest
```
## Run image that includes data

To simplify development, we have provided a Docker image that comes pre-loaded with image data and tasks. Example images are from the [WAID dataset from Applied Sciences](https://github.com/xiaohuicui/WAID/).

Note that this version of Scout does not include Scoutbot and therefore does not require a GPU to function. This also means, however, that it cannot process images with ML classifiers.

#### One time setup
From root of the code directory (`/scout`), run `npm install` to make sure all necessary libraries are installed.

#### Usage
1. `cd` to the `/develop-with-data` directory
1. Run `docker-compose up` to fetch that docker image and run Scout.
1. Once running, use a browser to open http://localhost:1337
1. Login with `admin`/`admin` as username/password.

#### Troubleshooting
- If you encounter a docker error `urllib3.exceptions.URLSchemeUnknown: Not supported URL scheme http+docker`, try running `pip install requests=2.31.0`
- If your process fails, you should run `docker-compose down` to stop the container when you shut down your scout instance (`Ctrl+C`)
