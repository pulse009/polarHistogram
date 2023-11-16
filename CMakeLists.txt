cmake_minimum_required(VERSION 3.6)
project(test)

set(CMAKE_CXX_STANDARD 11)

find_package(glfw3 REQUIRED)
include_directories(${GLFW_INCLUDE_DIRS})
link_libraries(${GLFW_LIBRARY_DIRS})

find_package(OpenGL REQUIRED)
include_directories(${OPENGL_INCLUDE_DIRS})

find_package(GLEW REQUIRED)
include_directories(${GLEW_INCLUDE_DIRS})

set(IMPLOT_SOURCES
    implot/src/implot_demo.cpp
    implot/include/implot_internal.h
    implot/src/implot_items.cpp
    implot/src/implot.cpp
    implot/include/implot.h
)

add_library(implot STATIC ${IMPLOT_SOURCES}) #adding implot from subdirectory as lib

add_subdirectory(imgui)

include_directories(${PROJECT_SOURCE_DIR})
add_executable(${PROJECT_NAME} main.cpp)
target_link_libraries(${PROJECT_NAME} imgui)
target_link_libraries(${PROJECT_NAME} implot)


target_link_libraries(
        ${PROJECT_NAME}
        glfw
        GLEW::glew
        ${OPENGL_LIBRARIES}
        ${EXTRA_LIBS}
)