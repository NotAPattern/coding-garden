cmake_minimum_required(VERSION 3.14)
project(karatsev_nikita_game)

set(CMAKE_CXX_STANDARD 14)
#set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O0 -Wall -Werror -Wextra -Wzero-as-null-pointer-constant -Winit-self -Wswitch-default -Wfloat-equal -Wno-unused-parameter -fPIC -march=native")

list(APPEND CMAKE_MODULE_PATH "${PROJECT_SOURCE_DIR}/CMake")

find_package(BearLibTerminal REQUIRED)
include_directories(SYSTEM ${BLT_INCLUDE_DIRS})

set(PROJECT_HEADERS_DIR ${PROJECT_SOURCE_DIR}/includes)
set(PROJECT_SOURCES_DIR ${PROJECT_SOURCE_DIR}/src ${PROJECT_SOURCE_DIR})

file(GLOB_RECURSE HEADERS ${PROJECT_HEADERS_DIR}/*.h)
file(GLOB_RECURSE SOURCES ${PROJECT_SOURCES_DIR}/*.cpp)

add_executable(${PROJECT_NAME} ${HEADERS} ${SOURCES})

include_directories(${PROJECT_HEADERS_DIR})

target_link_libraries(${PROJECT_NAME} ${BLT_LIBRARIES})

file(COPY ${BLT_LIBRARY} DESTINATION ${CMAKE_CURRENT_BINARY_DIR})

# Add linting before compilation
#include(CppLint)
#ADD_STYLE_CHECK_TARGET(lint ${PROJECT_NAME} ${PROJECT_HEADERS_DIR} ${PROJECT_SOURCES_DIR})
#add_dependencies(${PROJECT_NAME} lint)

# Target properties
#set_target_properties(karatsev_nikita_game PROPERTIES LINKER_LANGUAGE C)