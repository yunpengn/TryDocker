# TryDocker

This repository helps me to learn [Docker](https://www.docker.com). It contains some explanations, which could be useful to beginners. It also contains an example on how to setup a simple [Rails](https://rubyonrails.org) web application with [PostgreSQL](https://postgresql.org) using Docker.

## Why Docker?

There are a few technologies and/or softwares to be compared as follows:

- **[Docker](https://www.docker.com)**: a container-based virtualization solution that helps to develop, deploy and run application seamlessly. A container provides an independent environment to run an application, but under the same operating system. It takes almost no more resource than running the application natively. The diagrams below are taken from a research [paper](https://domino.research.ibm.com/library/cyberdig.nsf/papers/0929052195DD819C85257D2300681E7B/$File/rc25482.pdf) from IBM.
	- CPU performance tested using [LINPACK](http://www.netlib.org/linpack/)<br>
	![Linpack performance](img/linpack.png)
	- Sequential I/O throughput<br>
	![Sequential IO](img/sequence_io.png)
- Virtual Machine (VM): 

## Writing `Dockerfile`

Below are some tips for writing a `Dockerfile` with best practices:

- Do not include irrelevant files (_or libraries, tools_) inside the build context (the working directory when running the `docker build` command). This will result in a larger image size.
- Use a `.dockerignore` file to exclude those irrelevant files.
- Make sure the generated container is self-contained. People should be able to use it with minimum setup.
- Create the right number of layers rather than minimize the number of layers (due to multi-stage builds).
- Use `apt-get install -y` rather than `apt-get upgrade`.
- Always combine `apt-get update` with `apt-get install` in the same `RUN` statement.
- Prefer `COPY` over `ADD`, unless you need automatic tarball extraction.

## Acknowledgements

- [Docker Official Documentation](https://docs.docker.com)
	- [Best practices for writing Dockerfiles](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)
- [An Updated Performance Comparison of Virtual Machines and Linux Containers](https://domino.research.ibm.com/library/cyberdig.nsf/papers/0929052195DD819C85257D2300681E7B/$File/rc25482.pdf)

## Licence

[GNU General Public Licence 3.0](LICENSE)
