# Mutator-Driven Object Placement using Load Barriers

This repository contains the implementation of LR-Z used in the paper [Mutator-Driven Object Placement using Load Barriers](https://doi.org/10.1145/3679007.3685060).

## Comparing patches

`lr-z` contains the main contribution.

* [LR-Z patch](https://github.com/JonasNorlinder/lrz-mplr24/compare/jdk...lr-z) ...
or `git diff jdk lr-z`
* [Telemetry patch for ZGC](https://github.com/JonasNorlinder/lrz-mplr24/compare/jdk...jdk_telemetry) ...
or `git diff jdk jdk_telemetry`
* [Telemetry patch for LR-Z](https://github.com/JonasNorlinder/lrz-mplr24/compare/lr-z...lr-z_telemetry) ...
or `git diff lr-z lr-z_telemetry`

Note that `lr-z` also contains an extraction of the best configuration from [HCSGC](https://doi.org/10.1145/3385412.3385977). Use the following flags to activate different GCs:
* ZGC `-XX:+UseZGC`
* HCSGC `-XX:+UseZGC -XX:+UseRelocateAllSmallPages -XX:+UseLazyRelocate`
* LR-Z `-XX:+UseZGC -XX:+UsePartialEvacuation -XX:+UseLazyRelocate`

All GCs except HCSGC/LR-Z were evaluated using [JDK 15+36](https://github.com/openjdk/jdk/releases/tag/jdk-15%2B36) which can be found in the branch `jdk`.

## Notes on building
To configure building you should run (after checking out a branch) `bash configure --with-boot-jdk=/home/user/jdk/candidates/jdk-15.0.2 --with-extra-cxxflags='-std=c++11'`. To build you run `make CONF=release`.

`boot-jdk` needs to be version 14 or 15 and can be downloaded from https://jdk.java.net/archive/. Note that we only support Linux/x86.
