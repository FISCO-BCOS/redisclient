set(BENCHMARKS
    redis-parser-benchmark.cpp
)
find_package(Boost CONFIG REQUIRED program_options)

foreach(BENCHMARK ${BENCHMARKS})
  get_filename_component(EXECUTABLE ${BENCHMARK} NAME_WE)
  add_executable(${EXECUTABLE} ${BENCHMARK})
  target_link_libraries(${EXECUTABLE}
    RedisClient
    -lbenchmark
    -lprofiler
  )
endforeach()
