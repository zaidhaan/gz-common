cmake_minimum_required(VERSION 2.8 FATAL_ERROR)

# Find the gz-common library
find_package(gz-common5 QUIET REQUIRED COMPONENTS events profiler)
set(GZ_COMMON_VER ${gz-common5_VERSION_MAJOR})

add_executable(assert_example assert_example.cc)
target_link_libraries(assert_example gz-common${GZ_COMMON_VER}::core)

add_executable(console_example console.cc)
target_link_libraries(console_example gz-common${GZ_COMMON_VER}::core)

add_executable(events_example events.cc)
target_link_libraries(events_example gz-common${GZ_COMMON_VER}::events)

add_executable(profiler_example profiler.cc)
target_link_libraries(profiler_example gz-common${GZ_COMMON_VER}::profiler)
target_compile_definitions(profiler_example PUBLIC "GZ_PROFILER_ENABLE=1")

add_executable(logging_performance logging_performance.cc)
target_link_libraries(logging_performance gz-common${GZ_COMMON_VER}::core)

