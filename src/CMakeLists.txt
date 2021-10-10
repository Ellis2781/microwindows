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

add_library(libnano-X STATIC IMPORTED)
add_library(mwimages STATIC IMPORTED)
add_library(mwin STATIC IMPORTED)


set_target_properties(libnano-X PROPERTIES IMPORTED_LOCATION ${PROJECT_BINARY_DIR}/src/microwindows/src/lib/libnano-X.a)
set_target_properties(mwimages PROPERTIES IMPORTED_LOCATION ${PROJECT_BINARY_DIR}/src/microwindows/src/lib/libmwimages.a)
set_target_properties(mwin PROPERTIES IMPORTED_LOCATION ${PROJECT_BINARY_DIR}/src/microwindows/src/lib/libmwin.a)

target_link_libraries(libnano-X INTERFACE muslc)
target_link_libraries(mwimages INTERFACE muslc)
target_link_libraries(mwin INTERFACE muslc) 

add_executable(nano-X IMPORTED ${PROJECT_BINARY_DIR}/src/microwindows/src/bin/nano-X)
