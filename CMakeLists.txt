cmake_minimum_required(VERSION 3.27.7)
project(polarHist)

set(CMAKE_CXX_STANDARD 17)

find_package(glfw3 REQUIRED)
find_package(OpenGL REQUIRED)
find_package(GLEW REQUIRED)

add_subdirectory(src/imgui)

add_executable(${PROJECT_NAME} polarHist.h main.cpp)

target_include_directories(${PROJECT_NAME} PRIVATE
    ${PROJECT_SOURCE_DIR}
    "${PROJECT_SOURCE_DIR}/src/imgui"
    "${PROJECT_SOURCE_DIR}/src/imgui/backends"
    ${GLEW_INCLUDE_DIRS}
    ${OPENGL_INCLUDE_DIRS}
    ${GLFW_INCLUDE_DIRS}
)

target_link_libraries(
    ${PROJECT_NAME} 
    glfw 
    GLEW::glew
    ${OPENGL_LIBRARIES}
    ${EXTRA_LIBS}
    imgui 
)