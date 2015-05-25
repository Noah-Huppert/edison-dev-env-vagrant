#Intel Edison development environment
A Vagrant setup for a Intel Edison development environment

#Usage
To start the Vagrant virtual machine run

```bash
vagrant up
```

If it is your first time starting the virtual machine Vagrant will setup the machine with numerous C build tools and the Intel Edison SDK

#Development environment
The virtual machine comes with the following installed and configured

- Intel Edison SDK
- Ubuntu trusty 64 default packages and
  - unzip
  - gcc
  - g++
  - gcc-multilib
  - build-essentials
  - make
  - automake
