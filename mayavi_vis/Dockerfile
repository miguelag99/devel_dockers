FROM python:3.8

# Create user and install sudo
RUN useradd -m robesafe -d /home/robesafe -s /bin/bash -g root -G sudo -u 1000
RUN echo "robesafe:container"| chpasswd
RUN usermod -aG sudo robesafe
RUN apt update
RUN apt install sudo


RUN apt-get update
RUN apt-get install -y libgl1-mesa-glx mesa-utils libglapi-mesa
# RUN apt-get install python3
RUN python -m pip install --upgrade pip

RUN apt-get install python3-vtk7 -y

RUN mkdir /home/robesafe/.cache
COPY requirements.txt /home/robesafe/.cache
RUN pip install -r /home/robesafe/.cache/requirements.txt

WORKDIR /home/robesafe
USER robesafe

ENTRYPOINT /bin/bash
