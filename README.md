# baseimage
Docker base images for other projects

Image Dockerfiles are divided by branches. Each branch is a different image.

Why?
Because of Drone build CI. Drone has an easy way to starting builds per branch.

To test out Dockerfile commands, use
`docker run --rm -it node:18.13.0-bullseye sh`
