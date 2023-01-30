FROM node:18.13.0-bullseye

#Use an entrypoint that simply lists out all commands sent to it
COPY entryPoint.sh /src/fab/entryPoint.sh
ENTRYPOINT ["/src/fab/entryPoint.sh"]

#node:18 image already has a user node with uid:gid 1000:1000
#We add it to sudo list
RUN apt-get update \
    && apt-get install -y sudo less \
    && rm -rf /var/lib/apt/lists/* \
    && usermod -aG sudo node \
    && echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers \
#Creating a few base folders that child dockers may need
    && mkdir -p /src && chown node /src \
    && mkdir -p /cloud && chown node /cloud \
    && mkdir -p /build && chown node /build \
    && npm install -g pnpm \
    # upgrade pnpm to latest version
    && pnpm add -g pnpm

USER node

RUN echo 'alias p="pnpm"' >> ~/.bashrc

WORKDIR /src

#Allow image to be used standalone without any commands:
CMD ["tail", "-f", "/dev/null"]
#CMD ["sleep", "inf"]
