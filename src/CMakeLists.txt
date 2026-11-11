add_library(mmul_cpu)

target_sources(mmul_cpu
    PRIVATE
        cpu/Matrix.cpp

    PUBLIC
        FILE_SET header_mmul_cpu
        TYPE HEADERS
        BASE_DIRS
            ../include/cpu
        FILES
            ../include/cpu/Matrix.hpp
)


add_library(mmul_gpu_naive)

target_sources(mmul_gpu_naive
    PRIVATE
        gpu/Matrix.cu
        gpu/kernels/naive.cu

    PUBLIC
        FILE_SET header_mmul_gpu_naive
        TYPE HEADERS
        BASE_DIRS
            ../include/gpu
        FILES
            ../include/gpu/Matrix.cuh
            ../include/gpu/kernels.cuh
)