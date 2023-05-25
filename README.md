# Allpix2
Tutorials on Allpix2 simulation framework and Docker

### Please see this relevant documentation:

**[Docker](https://docs.docker.com/)**

**[Allpix2 Documentation](https://project-allpix-squared.web.cern.ch/usermanual/allpix-manual.pdf)**

**[Allpix2 gitlab](https://gitlab.cern.ch/allpix-squared/allpix-squared)**

## Docker


For absolute simplicity, you make think of docker as a light weight virtual machine (VM). As
opposed to a regular VM, docker uses less resources and is easily installed without needing to
dedicate significant portions of disk space to it. Docker uses containers, these are the things most
like a VM, where the container runs apps and/or other general software. For example, you can run Ubuntu in a container. One of the things to keep in mind with Docker is how to get
file (data) out of the container and onto your local drives. This is not something that is done
automatically and requires the user to mount a drive with the command 
