cmake_minimum_required(VERSION 3.15)

# set the project name and version
project(Tutorial VERSION 1.0)

SET(SRC_LIST tutorial.cpp)

# specify the C++ standard
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# pass version information to Config
configure_file(TutorialConfig.h.in TutorialConfig.h)

MESSAGE(STATUS "This is BINARY dir " ${Tutorial_BINARY_DIR})
MESSAGE(STATUS "This is SOURCE dir " ${Tutorial_SOURCE_DIR})
MESSAGE(STATUS "Project binary dir " ${PROJECT_BINARY_DIR})
MESSAGE(STATUS "Project SOURCE dir " ${PROJECT_SOURCE_DIR})

# add the MathFunctions library
add_subdirectory(MathFunctions)


# add the executable
add_executable(${PROJECT_NAME} ${SRC_LIST})


#LINK_DIRECTORIES(${PROJECT_SOURCE_DIR}/MathFunctions)

target_link_libraries(${PROJECT_NAME} PUBLIC MathFunctions)

#  include_directories() is accessible for all the files in the source-tree
#INCLUDE_DIRECTORIES(${PROJECT_SOURCE_DIR}/MathFunctions)

# target_include_directories() is-only accessible for a specific target
# and it will populate the INTERFACE_INCLUDE_DIRECTORIES property of the target when defined with PUBLIC/INTERFACE.

# comes after the executable definition
# add the binary tree to the search path for include files
# so that we will find TutorialConfig.h
target_include_directories(${PROJECT_NAME} PUBLIC
                           ${PROJECT_BINARY_DIR}
                           # already declared in CMakeLists.txt of the MathFunctions library
                           #${PROJECT_SOURCE_DIR}/MathFunctions
                           )
