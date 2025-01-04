# docker_files

## Ubuntu installation steps

### Add Docker's official GPG key:
```
sudo apt update
sudo apt install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
```

### Add the repository to apt sources:
```
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
```

### Install

```sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin```


## Available Docker files

### ubuntu_cpp

Based on `ubuntu` image. Uses GCC version 14.

### esp8266

Build environment for ESP8266 with [ESP8266_RTOS_SDK](https://github.com/espressif/ESP8266_RTOS_SDK). Adds a Python virtual environment with necessary dependencies.

To start a container in the interactive mode, run the command below. Device is usually named `ttyUSB0`. Change it if necessary.

```
docker run -it --device /dev/ttyUSB0:/dev/ttyUSB0 -e ESPPORT="/dev/ttyUSB0" esp8266
```

## Use with Visual Studio Code

Make sure following extensions are installed:

  * Docker
  * Dev Containers
  * CMakeTools

From the IDE, open the folder with your CMake project.
See [sample ESP8266 project](https://github.com/mapi-ng/esp8266_cmake_template).

Using _Dev Containers_ extension, _Attach to Running Container..._ and select the container started in previous step.
