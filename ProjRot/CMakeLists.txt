cmake_minimum_required(VERSION 3.7)
project(projrot C)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/bin")

add_library(ProjRotLibs
    src/eigen2.c
    src/eigen.c
    src/nrutil.c
    src/spline.c
    src/invert_matrix3.c)

add_executable(${PROJECT_NAME} src/main.c)

target_link_libraries(${PROJECT_NAME} ProjRotLibs m)

include(GNUInstallDirs)
install(
    TARGETS ${PROJECT_NAME}
    EXPORT ${PROJECT_NAME}Targets
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
    RUNTIME DESTINATION ${BINDIR}
)
