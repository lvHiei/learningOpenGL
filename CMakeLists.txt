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
set(TEXTURES_SRC_PATH ${SRC_PATH}/textures)

include_directories(${GLFE_INCLUDE_PATH})
include_directories(${GLFE_DEPS_PATH})
include_directories(${SRC_PATH})

set(COMMON_SRCS 
    ${SRC_PATH}/glad.c 
    ${SRC_PATH}/learn_def.h 
    ${SRC_PATH}/shader_s.h
    ${SRC_PATH}/stb_image.h)

add_executable(helloWindow ${HELLOWINDOW_SRC_PATH}/helloWindow.cpp ${SRC_PATH}/glad.c)
target_link_libraries(helloWindow ${COMMON_LIBS})

add_executable(helloTriangle ${HELLOTRIANGLE_SRC_PATH}/helloTriangle.cpp ${SRC_PATH}/glad.c)
target_link_libraries(helloTriangle ${COMMON_LIBS})

add_executable(helloTriangleIndexed ${HELLOTRIANGLE_SRC_PATH}/helloTriangleIndexed.cpp ${SRC_PATH}/glad.c)
target_link_libraries(helloTriangleIndexed ${COMMON_LIBS})

add_executable(shaders_uniform ${SHADERS_SRC_PATH}/shaders_uniform.cpp ${SRC_PATH}/glad.c)
target_link_libraries(shaders_uniform ${COMMON_LIBS})

add_executable(shaders_interpolation ${SHADERS_SRC_PATH}/shaders_interpolation.cpp ${SRC_PATH}/glad.c)
target_link_libraries(shaders_interpolation ${COMMON_LIBS})

add_executable(shaders_class ${SHADERS_SRC_PATH}/shaders_class.cpp ${COMMON_SRCS})
target_link_libraries(shaders_class ${COMMON_LIBS})

add_executable(textures ${TEXTURES_SRC_PATH}/textures.cpp ${COMMON_SRCS})
target_link_libraries(textures ${COMMON_LIBS})

add_executable(textures_combined ${TEXTURES_SRC_PATH}/textures_combined.cpp ${COMMON_SRCS})
target_link_libraries(textures_combined ${COMMON_LIBS})






set(EXERCISE_PATH ${CMAKE_SOURCE_DIR}/exercise)
set(E_HELLOTRIANGLE_PATH ${EXERCISE_PATH}/helloTriangle)
set(E_SHADERS_PATH ${EXERCISE_PATH}/shaders)
set(E_TEXTURES_PATH ${EXERCISE_PATH}/textures)

add_executable(e_helloTriangle1 ${E_HELLOTRIANGLE_PATH}/helloTriangle1.cpp ${SRC_PATH}/glad.c)
target_link_libraries(e_helloTriangle1 ${COMMON_LIBS})

add_executable(e_helloTriangle2 ${E_HELLOTRIANGLE_PATH}/helloTriangle2.cpp ${SRC_PATH}/glad.c)
target_link_libraries(e_helloTriangle2 ${COMMON_LIBS})

add_executable(e_helloTriangle3 ${E_HELLOTRIANGLE_PATH}/helloTriangle3.cpp ${SRC_PATH}/glad.c)
target_link_libraries(e_helloTriangle3 ${COMMON_LIBS})

add_executable(e_shaders1 ${E_SHADERS_PATH}/shaders1.cpp ${COMMON_SRCS})
target_link_libraries(e_shaders1 ${COMMON_LIBS})

add_executable(e_shaders2 ${E_SHADERS_PATH}/shaders2.cpp ${COMMON_SRCS})
target_link_libraries(e_shaders2 ${COMMON_LIBS})

add_executable(e_shaders3 ${E_SHADERS_PATH}/shaders3.cpp ${COMMON_SRCS})
target_link_libraries(e_shaders3 ${COMMON_LIBS})

add_executable(e_textures2 ${E_TEXTURES_PATH}/textures2.cpp ${COMMON_SRCS})
target_link_libraries(e_textures2 ${COMMON_LIBS})

add_executable(e_textures3 ${E_TEXTURES_PATH}/textures3.cpp ${COMMON_SRCS})
target_link_libraries(e_textures3 ${COMMON_LIBS})

add_executable(e_textures4 ${E_TEXTURES_PATH}/textures4.cpp ${COMMON_SRCS})
target_link_libraries(e_textures4 ${COMMON_LIBS})





#add_subdirectory(${GLFW_PATH})
