add_executable(mmul_tests)

target_sources(mmul_tests
    PRIVATE
        cpu_tests.cpp
        gpu_naive_tests.cu
)

find_package(GTest REQUIRED)

target_link_libraries(mmul_tests
    PRIVATE
        mmul_cpu
        mmul_gpu_naive
        gtest_main
        gtest
)

enable_testing()
include(GoogleTest)
gtest_discover_tests(mmul_tests)