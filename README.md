# Allpix2 Tutorial
Tutorials on Allpix2 simulation framework and Docker

### Please see this relevant documentation:

**[Docker](https://docs.docker.com/)**

**[Allpix2 Documentation](https://project-allpix-squared.web.cern.ch/usermanual/allpix-manual.pdf)**

**[Allpix2 gitlab](https://gitlab.cern.ch/allpix-squared/allpix-squared)**

## Docker


For absolute simplicity, you make think of docker as a light weight virtual machine (VM). As opposed to a regular VM, docker uses less resources and is easily installed without needing to dedicate significant portions of disk space to it. Docker uses containers, these are the things most like a VM, where the container runs apps and/or other general software. For example, you can run Ubuntu in a container. The major advantage with Docker for us is the **dependencies**, a docker image has all the dependencies included in it so you don't need to worry about getting ROOT, Geant4, Boost.Random, and Eigen3. To compile from source you'd have to have all 4 of these dependencies installed and working nicely *with* Allpix2, it would be an ardious task. Docker image has all of them included and working together off the rip.

One of the things to keep in mind with Docker is how to get files (data) out of the container and onto your local drives. This is not something that is done automatically and requires the user to mount a local drive with the command:
```
--volume "$(pwd)":/data
```

This is seen in the Allpix2 documentation on Docker images: 

"Docker images are provided for all releases and the latest development version of the framework.
To create a container from the latest Docker image and start an interactive shell session with the current host system path mounted to `/data`, run:

```shell
$ docker run --interactive --tty --volume "$(pwd)":/data --name=allpix-squared gitlab-registry.cern.ch/allpix-squared/allpix-squared bash
```

Alternatively it is also possible to directly start the simulation instead of an interactive shell:

```shell
$ docker run --tty --rm --volume "$(pwd)":/data --name=allpix-squared gitlab-registry.cern.ch/allpix-squared/allpix-squared "allpix -c my_simulation.conf"
```

To run a tagged version, append the tag to the image name, e.g. `gitlab-registry.cern.ch/allpix-squared/allpix-squared:v2.2.1`.
More detailed information on the Docker images can be found in the user manual."


## Allpix2

The framework is configured with simple human-readable configuration files, Section 4.3 of the documentation describes their format. **There are 3 main configuration files**, 

- **main configuration file:** most important, file that is passed directly to the binary. An example of this type of config file can be found in examples/example.conf

- **geometry configuration file:** It is passed to the framework to determine the detector setup and passive materials. This file describes detector position, orientation, and model type of all detectors. Examples of this type of config file are located at examples/example_detector.conf. 

- **detector model configuration file:** Contains parameters describing a particular type of detector. You may create your own type of detector within these files or use default detectors that are provided by the framework. See models/test.conf for an example.