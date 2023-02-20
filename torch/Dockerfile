FROM nvcr.io/nvidia/pytorch:22.11-py3

# Create user and install sudo
RUN useradd -m robesafe -d /home/robesafe -s /bin/bash -g root -G sudo -u 1000
RUN echo "robesafe:container"| chpasswd
RUN usermod -aG sudo robesafe
RUN apt update
RUN apt install sudo
USER robesafe

RUN python -m pip install --upgrade pip

RUN mkdir /home/robesafe/.cache
COPY requirements.txt /home/robesafe/.cache
RUN pip install -r /home/robesafe/.cache/requirements.txt

WORKDIR /home/robesafe

ENTRYPOINT /bin/bash
