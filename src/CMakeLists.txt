cmake_minimum_required(VERSION 3.0.0)

project(microwindows)

include(ExternalProject)

ExternalProject_Add(
    microwindows
    PREFIX ${PROJECT_BINARY_DIR}
    GIT_REPOSITORY https://github.com/Ellis2781/microwindows/
    UPDATE_DISCONNECTED true
    BUILD_COMMAND make -C ${PROJECT_BINARY_DIR}/src/microwindows/src
    INSTALL_COMMAND make -C ../microwindows/src
)

