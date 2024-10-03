FROM tensorflow/tensorflow:2.17.0-gpu

COPY gpu/requirements.txt /tmp

RUN apt update && apt install python3-pip -y

RUN python3 -m pip install --no-cache-dir -r /tmp/requirements.txt

COPY . .

ENTRYPOINT ["deepspeech-server", "--config", "/opt/deepspeech/config.yaml"]