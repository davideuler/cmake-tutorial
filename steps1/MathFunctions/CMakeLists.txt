# MathFunctions/CMakeLists.txt
add_library(MathFunctions SHARED mysqrt.cpp)

# Define interface for consumers of the library
# MathFunctions/CMakeLists.txt
target_include_directories(MathFunctions
          INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}
          )
