
cmake_minimum_required(VERSION 3.1.0 FATAL_ERROR)

list(APPEND CMAKE_PREFIX_PATH
    $ENV{USER_DEVELOP}/opencv/build-litiv/install/ $ENV{USER_DEVELOP}/opencv/build/install $ENV{USER_DEVELOP}/opencv/
    $ENV{USER_DEVELOP}/freeglut/build-litiv/install/ $ENV{USER_DEVELOP}/freeglut/build/install $ENV{USER_DEVELOP}/freeglut/
    $ENV{USER_DEVELOP}/glfw/build-litiv/install/ $ENV{USER_DEVELOP}/glfw/build/install $ENV{USER_DEVELOP}/glfw/
    $ENV{USER_DEVELOP}/glew/build-litiv/install/ $ENV{USER_DEVELOP}/glew/build/install $ENV{USER_DEVELOP}/glew/
    $ENV{USER_DEVELOP}/glm/build-litiv/install/ $ENV{USER_DEVELOP}/glm/build/install $ENV{USER_DEVELOP}/glm/
    $ENV{USER_DEVELOP}/opengm/build-litiv/install/ $ENV{USER_DEVELOP}/opengm/build/install $ENV{USER_DEVELOP}/opengm/
)

################################################################

project(litiv-ext-test)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
if(WIN32)
    if(MSVC AND (MSVC_VERSION LESS 1900))
        message(FATAL_ERROR "MSVC toolchains older than 2015 (v140) are not supported!")
    endif()
endif()

find_package(litiv REQUIRED)

add_executable(litiv-ext-test main.cpp)
target_link_libraries(litiv-ext-test litiv_world)
target_include_directories(litiv-ext-test
    PUBLIC
        ${LITIV_EXT_INCLUDE_DIRS}
)

