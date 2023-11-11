cmake_minimum_required(VERSION 3.27)

project(milkv_duo_sandbox)

# Generic ARM build
set(CMAKE_SYSTEM_NAME Generic)
set(CMAKE_SYSTEM_PROCESSOR arm)

# Set our sysroot location for libraries we need to link
set(SYSROOT_PATH "/opt/duo-sdk/rootfs")

# Set our compiler (generic location)
set(CMAKE_C_COMPILER "/opt/duo-sdk/riscv64-linux-musl-x86_64/bin/riscv64-unknown-linux-musl-gcc")
set(CMAKE_CXX_COMPILER "/opt/duo-sdk/riscv64-linux-musl-x86_64/bin/riscv64-unknown-linux-musl-g++")

# Compile and link flags from duo examples
set(GENERIC_FLAGS "-mcpu=c906fdv -march=rv64imafdcv0p7xthead -mcmodel=medany -mabi=lp64d")

set(CMAKE_C_FLAGS ${GENERIC_FLAGS})
set(CMAKE_CXX_FLAGS ${GENERIC_FLAGS})
set(CMAKE_EXE_LINKER_FLAGS ${GENERIC_FLAGS})

# Compiler definitions from duo examples
add_compile_definitions(
    _LARGEFILE_SOURCE
    _LARGEFILE64_SOURCE 
    _FILE_OFFSET_BITS=64
)

add_subdirectory(test-project)