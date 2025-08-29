cmake_minimum_required(VERSION 3.16)
project(Game-Engine-Project LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(BUILD_SHARED_LIBS OFF CACHE BOOL "" FORCE)        
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_INSTALL OFF CACHE BOOL "" FORCE)

# Add GLFW (submodule) to the build
add_subdirectory(external/glfw)

# Find OpenGL (portable target: OpenGL::GL)
find_package(OpenGL REQUIRED)

add_executable(${PROJECT_NAME} src/main.cpp)

# Link: GLFW + OpenGL
target_link_libraries(${PROJECT_NAME} PRIVATE glfw OpenGL::GL)

target_include_directories(${PROJECT_NAME} PRIVATE external/glfw/include)

# On macOS, request a modern OpenGL context & set bundle properties (optional)
if(APPLE)
    target_compile_definitions(${PROJECT_NAME} PRIVATE "GL_SILENCE_DEPRECATION")
endif()
