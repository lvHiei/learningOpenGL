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
set(HELLOWINDOW_SRC_PATH ${SRC_PATH}/helloWindow)
set(HELLOTRIANGLE_SRC_PATH ${SRC_PATH}/helloTriangle)
set(HELLOTRIANGLE2_SRC_PATH ${SRC_PATH}/helloTriangle2)

include_directories(${GLFE_INCLUDE_PATH})
include_directories(${GLFE_DEPS_PATH})

add_executable(helloWindow ${HELLOWINDOW_SRC_PATH}/helloWindow.cpp ${SRC_PATH}/glad.c)
target_link_libraries(helloWindow ${COMMON_LIBS})

add_executable(helloTriangle ${HELLOTRIANGLE_SRC_PATH}/helloTriangle.cpp ${SRC_PATH}/glad.c)
target_link_libraries(helloTriangle ${COMMON_LIBS})

add_executable(helloTriangle2 ${HELLOTRIANGLE2_SRC_PATH}/helloTriangle.cpp ${SRC_PATH}/glad.c)
target_link_libraries(helloTriangle2 ${COMMON_LIBS})



set(EXERCISE_PATH ${CMAKE_SOURCE_DIR}/exercise)

add_executable(e_helloTriangle1 ${EXERCISE_PATH}/helloTriangle1/helloTriangle1.cpp ${SRC_PATH}/glad.c)
target_link_libraries(e_helloTriangle1 ${COMMON_LIBS})

add_executable(e_helloTriangle2 ${EXERCISE_PATH}/helloTriangle2/helloTriangle2.cpp ${SRC_PATH}/glad.c)
target_link_libraries(e_helloTriangle2 ${COMMON_LIBS})

add_executable(e_helloTriangle3 ${EXERCISE_PATH}/helloTriangle3/helloTriangle3.cpp ${SRC_PATH}/glad.c)
target_link_libraries(e_helloTriangle3 ${COMMON_LIBS})
#add_subdirectory(${GLFW_PATH})
