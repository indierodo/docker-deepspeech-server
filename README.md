# Docker DeepSpeech Server
This is a dockerfile to serve a [deepspeech server](https://github.com/MainRo/deepspeech-server).

# How to use this image
Create a deepspeech server configuration file as specified in config.example.yaml. Download and copy
a model tflite and a scorer file and run the following command:

    docker run -dt --name deepspeech \
    -p 0.0.0.0:8080:8080 \
    -v [host-model-path]:/opt/deepspeech \
    romainsah/deepspeech-server:latest

where [host-model-path] is a host directory that contains the deepspeech server
configuration file (e.g. config.yaml), the model file (e.g. model.tflite), and the scorer file (e.g. huge-vocabulary.scorer).

## Running on GPU
Change the tag of the docker image in above command to latest-gpu, like this:

    docker run -dt --name deepspeech \
    -p 0.0.0.0:8080:8080 \
    -v [host-model-path]:/opt/deepspeech \
    romainsah/deepspeech-server:latest-gpu

## How to get the models

The latest docker image was tested with the following model and scorer files:

https://github.com/coqui-ai/STT-models/releases/download/english/coqui/v1.0.0-huge-vocab/model.tflite

https://github.com/coqui-ai/STT-models/releases/download/english/coqui/v1.0.0-huge-vocab/huge-vocabulary.scorer

## How to build this image

    cd cpu && \
    docker build -t deepspeech-server:latest

    cd gpu && \
    docker build -t deepspeech-server:latest-gpu