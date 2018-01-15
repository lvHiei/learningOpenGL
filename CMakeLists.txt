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
message("GLFW_GLFW_PATH is ${GLFW_SRC_PATH}")

if(NOT GLFW_SRC_PATH)
    message(FATAL_ERROR "Not Found GLFW_PATH")
endif()

set(GLFE_INCLUDE_PATH ${GLFW_SRC_PATH}/include)
set(GLFE_DEPS_PATH ${GLFW_SRC_PATH}/deps)

set(SRC_PATH ${CMAKE_SOURCE_DIR}/src)
set(HELLOWINDOW_SRC_PATH ${SRC_PATH}/1.1.helloWindow)
set(HELLOTRIANGLE_SRC_PATH ${SRC_PATH}/2.1.helloTriangle)
set(SHADERS_SRC_PATH ${SRC_PATH}/3.1.shaders)
set(TEXTURES_SRC_PATH ${SRC_PATH}/4.1.textures)
set(TRANSFORM_SRC_PATH ${SRC_PATH}/5.1.transformations)
set(COORDINATE_SYSTEM_SRC_PATH ${SRC_PATH}/6.1.coordinate_systems)

include_directories(${GLFE_INCLUDE_PATH})
include_directories(${GLFE_DEPS_PATH})
include_directories(${SRC_PATH})
include_directories(${SRC_PATH}/glm)

set(COMMON_SRCS 
    ${SRC_PATH}/glad.c 
    ${SRC_PATH}/learn_def.h 
    ${SRC_PATH}/shader_s.h
    ${SRC_PATH}/stb_image.h)

set(CMAKE_CXX_FLAGS ${CMAKE_CXX_FLAGS} -std=c++11)


add_executable(1.1.helloWindow ${HELLOWINDOW_SRC_PATH}/helloWindow.cpp ${SRC_PATH}/glad.c)
target_link_libraries(1.1.helloWindow ${COMMON_LIBS})

add_executable(2.1.helloTriangle ${HELLOTRIANGLE_SRC_PATH}/helloTriangle.cpp ${SRC_PATH}/glad.c)
target_link_libraries(2.1.helloTriangle ${COMMON_LIBS})

add_executable(2.2.helloTriangleIndexed ${HELLOTRIANGLE_SRC_PATH}/helloTriangleIndexed.cpp ${SRC_PATH}/glad.c)
target_link_libraries(2.2.helloTriangleIndexed ${COMMON_LIBS})

add_executable(3.1.shaders_uniform ${SHADERS_SRC_PATH}/shaders_uniform.cpp ${SRC_PATH}/glad.c)
target_link_libraries(3.1.shaders_uniform ${COMMON_LIBS})

add_executable(3.2.shaders_interpolation ${SHADERS_SRC_PATH}/shaders_interpolation.cpp ${SRC_PATH}/glad.c)
target_link_libraries(3.2.shaders_interpolation ${COMMON_LIBS})

add_executable(3.3.shaders_class ${SHADERS_SRC_PATH}/shaders_class.cpp ${COMMON_SRCS})
target_link_libraries(3.3.shaders_class ${COMMON_LIBS})

add_executable(4.1.textures ${TEXTURES_SRC_PATH}/textures.cpp ${COMMON_SRCS})
target_link_libraries(4.1.textures ${COMMON_LIBS})

add_executable(4.2.textures_combined ${TEXTURES_SRC_PATH}/textures_combined.cpp ${COMMON_SRCS})
target_link_libraries(4.2.textures_combined ${COMMON_LIBS})

add_executable(5.1.transformations ${TRANSFORM_SRC_PATH}/transformations.cpp ${COMMON_SRCS})
target_link_libraries(5.1.transformations ${COMMON_LIBS})

add_executable(6.1.coordinate_systems ${COORDINATE_SYSTEM_SRC_PATH}/coordinate_systems.cpp ${COMMON_SRCS})
target_link_libraries(6.1.coordinate_systems ${COMMON_LIBS})

add_executable(6.2.coordinate_systems_depth ${COORDINATE_SYSTEM_SRC_PATH}/coordinate_systems_depth.cpp ${COMMON_SRCS})
target_link_libraries(6.2.coordinate_systems_depth ${COMMON_LIBS})

add_executable(6.3.coordinate_systems_multiple ${COORDINATE_SYSTEM_SRC_PATH}/coordinate_systems_multiple.cpp ${COMMON_SRCS})
target_link_libraries(6.3.coordinate_systems_multiple ${COMMON_LIBS})



set(EXERCISE_PATH ${CMAKE_SOURCE_DIR}/exercise)
set(E_HELLOTRIANGLE_PATH ${EXERCISE_PATH}/2.1.helloTriangle)
set(E_SHADERS_PATH ${EXERCISE_PATH}/3.1.shaders)
set(E_TEXTURES_PATH ${EXERCISE_PATH}/4.1.textures)
set(E_TRANSFROMS_PATH ${EXERCISE_PATH}/5.1.transformations)
set(E_COORDINATE_SYSTEM_PATH ${EXERCISE_PATH}/6.1.coordinate_systems)

add_executable(e2_helloTriangle1 ${E_HELLOTRIANGLE_PATH}/helloTriangle1.cpp ${SRC_PATH}/glad.c)
target_link_libraries(e2_helloTriangle1 ${COMMON_LIBS})

add_executable(e2_helloTriangle2 ${E_HELLOTRIANGLE_PATH}/helloTriangle2.cpp ${SRC_PATH}/glad.c)
target_link_libraries(e2_helloTriangle2 ${COMMON_LIBS})

add_executable(e2_helloTriangle3 ${E_HELLOTRIANGLE_PATH}/helloTriangle3.cpp ${SRC_PATH}/glad.c)
target_link_libraries(e2_helloTriangle3 ${COMMON_LIBS})

add_executable(e3_shaders1 ${E_SHADERS_PATH}/shaders1.cpp ${COMMON_SRCS})
target_link_libraries(e3_shaders1 ${COMMON_LIBS})

add_executable(e3_shaders2 ${E_SHADERS_PATH}/shaders2.cpp ${COMMON_SRCS})
target_link_libraries(e3_shaders2 ${COMMON_LIBS})

add_executable(e3_shaders3 ${E_SHADERS_PATH}/shaders3.cpp ${COMMON_SRCS})
target_link_libraries(e3_shaders3 ${COMMON_LIBS})

add_executable(e4_textures2 ${E_TEXTURES_PATH}/textures2.cpp ${COMMON_SRCS})
target_link_libraries(e4_textures2 ${COMMON_LIBS})

add_executable(e4_textures3 ${E_TEXTURES_PATH}/textures3.cpp ${COMMON_SRCS})
target_link_libraries(e4_textures3 ${COMMON_LIBS})

add_executable(e4_textures4 ${E_TEXTURES_PATH}/textures4.cpp ${COMMON_SRCS})
target_link_libraries(e4_textures4 ${COMMON_LIBS})

add_executable(e5_transform2 ${E_TRANSFROMS_PATH}/transformations2.cpp ${COMMON_SRCS})
target_link_libraries(e5_transform2 ${COMMON_LIBS})

add_executable(e6_coordinateSystem3 ${E_COORDINATE_SYSTEM_PATH}/coordinate_systems.cpp ${COMMON_SRCS})
target_link_libraries(e6_coordinateSystem3 ${COMMON_LIBS})







#add_subdirectory(${GLFW_PATH})
