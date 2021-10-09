cmake_minimum_required(VERSION 3.0.0)

project(microwindows)

include(ExternalProject)

ExternalProject_Add(
    microwindows
    GIT_REPOSITORY https://github.com/Ellis2781/microwindows/
    UPDATE_DISCONNECTED true
    BUILD_COMMAND make -j${Ncpu}
    INSTALL_COMMAND make -j${Ncpu} install
)

