cmake_minimum_required(VERSION 3.10)
project(declaration VERSION 1.0 LANGUAGES CXX)

# specify the C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# add the executable
add_executable(declaration main.cpp)

file(GLOB MYLIB_SOURCES "${CMAKE_CURRENT_SOURCE_DIR}/MyClass/*.cpp")
file(GLOB MYLIB_HEADERS "${CMAKE_CURRENT_SOURCE_DIR}/MyClass/*.hpp")

add_library(mylibrary ${MYLIB_SOURCES} ${MYLIB_HEADERS})
target_link_libraries(declaration PRIVATE mylibrary)

# specify where the executable should be installed
install(TARGETS declaration DESTINATION bin)
