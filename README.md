# Node.js with OpenCV 4 Docker Image

This repository contains a Dockerfile for creating a Docker image equipped with Node.js and OpenCV 4.

## Prerequisites

Before building and running this Docker image, you must have Docker installed on your machine. To install Docker, follow the instructions for your operating system on the [official Docker website](https://docs.docker.com/get-docker/).

## Building the Docker Image

To build the Docker image from the Dockerfile, run the following command from the root directory of this repository:

```bash
docker build -t nodejs-opencv .
```

This command builds a Docker image named `nodejs-opencv` based on the instructions in the Dockerfile.

## Running the Docker Container

After the image has been successfully built, you can run a container using the following command:

```bash
docker run -it --name my-app nodejs-opencv
```

This command starts a container named `my-app` from the `nodejs-opencv` image. The `-it` option allows you to interact with the container through your terminal.

## What's Inside the Dockerfile

The Dockerfile in this repository is designed to set up an environment with the following:

- **Node.js**: A JavaScript runtime built on Chrome's V8 JavaScript engine.
- **OpenCV 4**: An open-source computer vision and machine learning software library.

The Dockerfile handles the following tasks:
- Installing necessary base libraries and tools.
- Installing Node.js.
- Building OpenCV 4 from source.
- Installing OpenCV4


## Contributing

Contributions to this repository are welcome. You can contribute by:
- Reporting a bug
- Submitting a fix
- Extending or adding new Dockerfiles for different versions of Node.js or OpenCV.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.