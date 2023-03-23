# Building-Container-Images-without-Dockerfiles

# Building Containers without Dockerfiles
Containers and their technology have revolutionized the way developers package, distribute and run software applications. Docker is one of the most popular tools in use todays to build and manage our containers, consequently, Dockerfiles are the go-to method for defining container images. However, they are just one option to create them, and there are other technologies that supersede the need of them.

# Buildah
Buildah is an open-source, Linux-based tool to build OCI (Open Container Initiative)-compatible containers. Buildah allows you to create, modify, and build container images without the need of a Dockerfile. 
## Why Buildah?
Buildah provides the flexibility of building images without Dockerfiles, allows for integration with other scripting languages into the building process. Images can now be created with ease and quickly with only the required tools and processes necessary.
Buildah allows you to
- Inspect, verify, and modify images
- Push containers and images from local storage to a public or private registry or repository
- Push or pull images from the Docker Hub
- Remove locally stored container images
- Mount and unmount a working container's root file system
- Use the updated contents of a container's root filesystem as a filesystem layer for a new image

## Building with Buildah instead of Docker
- The size of the created image is smaller
- Improved security of the image because the software used to create the container (such as gcc, make, and dnf) is not contained in the image.
- Fewer resources are required to move images owing to their smaller size.
- You can create a single layer image which can be more suited to test and production environments.
- Better secrets handling for subscriptions or credentials to secure registries.

## Use Buildah to Create New Containers
To get started with Buildah and build an httpd server the following instructions can be used.
- Create a Scratch Container
`buildah from scratch working-container
- Add Files
`buildah add working-container file.txt /`
- Install Packages
`buildah run working-container -- yum install -y httpd`
- Add text to html
`buildah echo "Container made from scratch" > index.html`
- Configure Container
`buildah config --entrypoint "/usr/sbin/httpd -DFOREGROUND" working-container`
`buildah config --port 80/tcp working-container`
`buildah commit working-container docer-daemon:myhttpd: latest`
- Commit Container
`buildah commit working-container working-image`

## Limitations to Buildah
- Buildah is primarily designed for Linux environments. Running it on other platforms requires other steps and does not offer the same level of functionality
- Buildah is limited to building and managing containers and does not provide support for container orchestration.

# Conclusion
Buildah is a tool that provides alternatives to Dockerfiles for building container images but it does not provide the full functionalities that are awarded by Docker.
