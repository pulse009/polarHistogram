cmake_minimum_required(VERSION 3.27.7)
project(polarHist)

set(CMAKE_CXX_STANDARD 23)

find_package(glfw3 REQUIRED)
find_package(OpenGL REQUIRED)
find_package(GLEW REQUIRED)
find_package(SDL2 REQUIRED)
# find_package(GLUT REQUIRED)

file(GLOB imgui_sources
    src/imgui/*.h
    src/imgui/*.cpp
    src/imgui/backends/*.h
    src/imgui/backends/*.cpp
)

add_executable(${PROJECT_NAME} polarHist.h main.cpp ${imgui_sources})

target_include_directories(${PROJECT_NAME} PRIVATE
    ${PROJECT_SOURCE_DIR}
    ${GLFW_INCLUDE_DIRS}
    ${OPENGL_INCLUDE_DIRS}
    ${GLEW_INCLUDE_DIRS}
    ${SDL2_INCLUDE_DIRS}
    # ${GLUT_INCLUDE_DIRS}
    ${PROJECT_SOURCE_DIR}/src/imgui
    ${PROJECT_SOURCE_DIR}/src/imgui/backends
)

target_link_libraries(
    ${PROJECT_NAME} 
    glfw 
    GLEW::glew
    ${OPENGL_LIBRARIES}
    ${EXTRA_LIBS}
    ${SDL2_LIBRARIES}
    # ${GLUT_LIBRARY}
)