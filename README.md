## ASCII ART

A set of scripts for rendering ascci art from images, can be run locally or via docker container.

### Docker Setup

Build the image
```
~$ docker build --tag:art:latest .
```

To run the container, it is necesary to mount two bind volumes so that the ouput can be inspected on the local machine
```
~$ docker run -it -e script_name=image_segmentation \
  --mount type=bind,source=$(pwd)/src/images/,target=/src/images/ \
  --mount type=bind,source=$(pwd)/src/output/,target=/src/output/ \
  --name=art \
  --rm \
  art:latest <arguments for script_name check above environment variable | default is -h for help>
```

Tested scripts for script_name environment variable currently are:
- [x] `image_segmentation` - Tested
- [ ] `swapper` - Not Tested
- [ ] `get_image` - Not Tested.
- [ ] `video_swapper` - Not Tested.


### Local Machine Setup

#### Requirements:

- Python3.8 >
- Debian (Ubuntu 18.04, 20.04) - Tested

Within the `/src` directory of the project, add a directory called `images`, within
this directory include all the images you want to conver to ascii. In addition, create
also within `/src` create another directory called `output` which will be where the rendered art
will be generated.


Install dependencies
```bash
:~$ python3.8 -m pip install -r requirements.txt
```

Depending on installation u might need to install `cv2` required libraries
```
apt-get update -y && \
    apt-get install -y \
    ffmpeg \
    libsm6 \
    libxext6
```

#### How To Use

Every script has it's own help menu and you can trigger it by running the script with
the --help flag

run the scripts from the `/src/bin` directory.

Usable Scripts:
- `image_segmentation`
- `download_image`
- `swapper`
