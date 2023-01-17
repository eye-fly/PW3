cmake_minimum_required (VERSION 3.1)
project (Cyrk CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_FLAGS "-std=c++20 -Wall -Wextra -Werror -pedantic -fsanitize=undefined,thread")

set(THREADS_PREFER_PTHREAD_FLAG TRUE)
find_package(Threads REQUIRED)
# find_package(Latchs REQUIRED)

function(add_example_program target_name)
  add_executable(${target_name} "${target_name}.cpp")
  target_link_libraries(${target_name} Threads::Threads)
endfunction()

add_library(system system.cpp)
add_example_program(demo)
target_link_libraries(demo system)