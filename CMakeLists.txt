cmake_minimum_required(VERSION 3.22.0)

project (Learn-LLVM-Core-Libraries-Second-Edition)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

find_package(LLVM REQUIRED CONFIG)
message(STATUS "Found LLVM ${LLVM_PACKAGE_VERSION}")
message(STATUS "Using LLVMConfig.cmake in: ${LLVM_DIR}")

add_definitions(${LLVM_DEFINITIONS})
include_directories(${LLVM_INCLUDE_DIRS})
link_directories(${LLVM_LIBRARY_DIRS})

include(AddLLVM)
add_executable(ch2_64bit_div "Chapter 2/ch2_64bit_div.c")
add_executable(ch3 "Chapter 3/main.c"
        "Chapter 3/sum.c"
)
add_executable(ch5_llvm_exception "Chapter 5/ch5_llvm_exception.cpp")
target_link_libraries(ch5_llvm_exception
        PRIVATE
        LLVMCore
        LLVMSupport
)
add_subdirectory("Chapter 6")