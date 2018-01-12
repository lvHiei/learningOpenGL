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
set(SHADERS_SRC_PATH ${SRC_PATH}/shaders)

include_directories(${GLFE_INCLUDE_PATH})
include_directories(${GLFE_DEPS_PATH})
include_directories(${SRC_PATH})

set(COMMON_SRCS ${SRC_PATH}/glad.c ${SRC_PATH}/learn_def.h ${SRC_PATH}/shader_s.h)

add_executable(helloWindow ${HELLOWINDOW_SRC_PATH}/helloWindow.cpp ${SRC_PATH}/glad.c)
target_link_libraries(helloWindow ${COMMON_LIBS})

add_executable(helloTriangle ${HELLOTRIANGLE_SRC_PATH}/helloTriangle.cpp ${SRC_PATH}/glad.c)
target_link_libraries(helloTriangle ${COMMON_LIBS})

add_executable(helloTriangle2 ${HELLOTRIANGLE_SRC_PATH}/helloTriangle2.cpp ${SRC_PATH}/glad.c)
target_link_libraries(helloTriangle2 ${COMMON_LIBS})

add_executable(shaders1 ${SHADERS_SRC_PATH}/shaders1.cpp ${SRC_PATH}/glad.c)
target_link_libraries(shaders1 ${COMMON_LIBS})

add_executable(shaders2 ${SHADERS_SRC_PATH}/shaders2.cpp ${SRC_PATH}/glad.c)
target_link_libraries(shaders2 ${COMMON_LIBS})

add_executable(shaders_class ${SHADERS_SRC_PATH}/shaders_class.cpp ${COMMON_SRCS})
target_link_libraries(shaders_class ${COMMON_LIBS})



set(EXERCISE_PATH ${CMAKE_SOURCE_DIR}/exercise)
set(E_HELLOTRIANGLE_PATH ${EXERCISE_PATH}/helloTriangle)

add_executable(e_helloTriangle1 ${E_HELLOTRIANGLE_PATH}/helloTriangle1.cpp ${SRC_PATH}/glad.c)
target_link_libraries(e_helloTriangle1 ${COMMON_LIBS})

add_executable(e_helloTriangle2 ${E_HELLOTRIANGLE_PATH}/helloTriangle2.cpp ${SRC_PATH}/glad.c)
target_link_libraries(e_helloTriangle2 ${COMMON_LIBS})

add_executable(e_helloTriangle3 ${E_HELLOTRIANGLE_PATH}/helloTriangle3.cpp ${SRC_PATH}/glad.c)
target_link_libraries(e_helloTriangle3 ${COMMON_LIBS})
#add_subdirectory(${GLFW_PATH})
