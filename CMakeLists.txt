cmake_minimum_required(VERSION 2.8.12)

project(learningOpenGL)

set(GLFW_LIBRARIES
    glfw3
    GL
    X11
    m
    dl
    pthread 
)

set(COMMON_LIBS
    ${GLFW_LIBRARIES}
)

set(GLFW_SRC_PATH $ENV{GLFW_PATH})
#set(GLFW_SRC_PATH $ENV{PATH})
message("GLFW_GLFW_PATH is ${GLFW_SRC_PATH}")
#message("GLFW_GLFW_PATH is $ENV{PATH}")

if(NOT GLFW_SRC_PATH)
    #    message(FATAL_ERROR "Not Found GLFW_PATH")
    set(GLFW_SRC_PATH /home/mj/disk/source/githup/glfw)
endif()

set(GLFE_INCLUDE_PATH ${GLFW_SRC_PATH}/include)
set(GLFE_DEPS_PATH ${GLFW_SRC_PATH}/deps)

set(SRC_PATH ${CMAKE_SOURCE_DIR}/src)
set(OFFSCREEN_SRC_PATH ${SRC_PATH}/offscreen)

include_directories(${GLFE_INCLUDE_PATH})
include_directories(${GLFE_DEPS_PATH})

#add_executable(offscreen ${OFFSCREEN_SRC_PATH}/offscreen.c ${OFFSCREEN_SRC_PATH}/myPng.c ${SRC_PATH}/glad.c)
#target_link_libraries(offscreen ${COMMON_LIBS})





#add_subdirectory(${GLFW_PATH})
