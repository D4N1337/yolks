FROM        --platform=$TARGETOS/$TARGETARCH mongo:6-focal

LABEL       author="Michael Parker" maintainer="parker@pterodactyl.io"

## install nodejs 18
RUN apt update && apt install --no-install-recommends -y curl \ 
 && curl -fsSL https://deb.nodesource.com/setup_18.x | bash - \
 && apt install -y nodejs \
 && npm install -g npm@latest \
 ## install bastion reqs
 && apt install -y python3 build-essential git libtool netcat ffmpeg iproute2 tzdata \
 ## add container user
 && useradd -d /home/container -m container -s /bin/bash

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

COPY        ./entrypoint.sh /entrypoint.sh
CMD         ["/bin/bash", "/entrypoint.sh"]