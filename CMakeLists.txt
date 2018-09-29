cmake_minimum_required(VERSION 3.8)
project(OpenGL CXX)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

#find_library(OpenGL REQUIRED)
find_package(OpenGL REQUIRED)
find_package(glfw3 REQUIRED)
find_package(Threads REQUIRED)

add_subdirectory("src/glad")

set(CMAKE_VERBOSE_MAKEFILE ON)
find_package(X11 REQUIRED)

set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)

message(STATUS ${OPENGL_FOUND}) 
message(STATUS ${GLFW_FOUND}) 
message(STATUS ${GLFW_INCLUDE_GLCOREARB}) 
add_executable(main "src/main")



target_link_libraries(main glfw)
target_link_libraries(main ${OPENGL_gl_LIBRARY})
target_link_libraries(main ${OPENGL_glu_LIBRARY})
target_link_libraries(main ${X11_LIBRARIES})
target_link_libraries(main ${CMAKE_THREAD_LIBS_INIT})
target_link_libraries(main glad)
target_link_libraries(main ${CMAKE_DL_LIBS})

 
