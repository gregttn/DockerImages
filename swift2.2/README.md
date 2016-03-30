#### To build the image

`docker build -t swift2.2 .`

#### To run the image

`docker run -i -t swift2.2 /bin/bash`

#### To run the image with current directory attached to /docs in the container

`docker run -v $(pwd):/docs -i -t swift2.2 /bin/bash`