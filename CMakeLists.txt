cmake_minimum_required(VERSION 3.18)

project(matrix_multiplication_cuda LANGUAGES CXX CUDA)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED OFF)
set(CMAKE_CUDA_STANDARD 17)
set(CMAKE_CUDA_STANDARD_REQUIRED OFF)
set(CMAKE_CUDA_ARCHITECTURES 86)
find_package(CUDAToolkit 12.0 REQUIRED OFF)


set(KERNEL_TYPE "naive" CACHE STRING "Type of kernel for matrix_multiplication_cuda (naive)")
set_property(CACHE KERNEL_TYPE PROPERTY STRINGS "naive")


add_subdirectory(src)
add_subdirectory(tests)
add_subdirectory(benchmarks)


add_executable(matrix_multiplication_cpu
    src/cpu/main.cpp
)
target_link_libraries(matrix_multiplication_cpu
    PRIVATE
        mmul_cpu
)

add_executable(matrix_multiplication_gpu
    src/gpu/main.cu
)
target_link_libraries(matrix_multiplication_gpu
    PRIVATE
        mmul_gpu_${KERNEL_TYPE}
)