add_executable(mmul_benchmarks)
target_sources(mmul_benchmarks
    PRIVATE
        cpu_bench.cpp
        gpu_naive_bench.cu
)

find_package(benchmark REQUIRED)

target_link_libraries(mmul_benchmarks
    PRIVATE
        mmul_cpu
        mmul_gpu_naive
        benchmark::benchmark
        benchmark::benchmark_main
        nvidia-ml
)

target_compile_options(mmul_benchmarks
    PRIVATE
        $<$<COMPILE_LANGUAGE:CUDA>:-O3>
        $<$<COMPILE_LANGUAGE:CXX>:-O3>
)