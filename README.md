# kernel-build-containers

This project provides Docker containers for building the Linux kernel (or other software) with many different compilers.

It's very useful for testing gcc-plugins for the Linux kernel, for example.

__Supported gcc versions (with `--enable-plugin`):__
 - gcc-4.8
 - gcc-5
 - gcc-6
 - gcc-7
 - gcc-8
 - gcc-9
 - gcc-10

__Supported build targets:__
 - `x86_64`
 - `i386`
 - `aarch64` (except gcc-4.8)

Idea for future: add Clang.

# Usage

Building all containers:

```console
$ sh build_containers.sh
```

Running a container:
 - get help
```console
$ sh run_container.sh
usage: ./run_container.sh gcc_version src_dir out_dir [cmd with args]
  if cmd is empty, we will start an interactive bash in the container
```

 - run interactive bash in the container
```console
$ sh run_container.sh 8 ~/linux/linux/ ~/linux/build_out/
Starting a container with GCC-8
Source code directory "/home/a13x/linux/linux/" is mounted at "~/src"
Build output directory "/home/a13x/linux/build_out/" is mounted at "~/out"
Gonna run interactive bash...
```

 - execute a command in the container
```console
$ sh run_container.sh 8 ~/linux/linux/ ~/linux/build_out/ gcc -v
Starting a container with GCC-8
Source code directory "/home/a13x/linux/linux/" is mounted at "~/src"
Build output directory "/home/a13x/linux/build_out/" is mounted at "~/out"
Gonna run "gcc -v"
```

Remove created docker images:

```console
$ sh rm_containers.sh
```


