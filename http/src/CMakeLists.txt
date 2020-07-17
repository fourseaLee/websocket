cmake_minimum_required(VERSION 2.8)

project(httpserver)

include_directories(./)

set(CMAKE_BUILD_TYPE "Debug")

set(basic_link_lib c rt pthread event event_pthreads)

set(server_src      httpserver.cpp
                    main.cpp)

add_executable(serverd ${server_src})

target_link_libraries(serverd ${basic_link_lib})

