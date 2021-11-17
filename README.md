# rtems-docker
A collection of Docker files for the RTEMS RTOS tools and BSP builds

Simiar to the RTEMS repositories, the branches support different versions of RTEMS:
- The default, or "main" branch supports the master branches of RTEMS tools and kernel source
- The "rtems4.11" branch supports RTEMS 4.11
- The "rtems5" branch supports the RTEMS 5 branch of the tools and RTEMS source

As new releases of RTEMS are made, the main will advance and a branch will be made for the release branch (rtems6 for example)

The images depend on each other:
- rtems6-essential - is the base image and tools
- rtems6-(arch)-tools - provides the RTEMS toolchain for that architecture
- rtems6-(arch)-(bsp) - provides a specific BSP build
