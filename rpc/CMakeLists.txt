cmake_minimum_required(VERSION 3.5)

project(librpc)

include_directories(./)
include_directories(../libhttp)

set(rpc_src src/protocol.cpp
            src/server.cpp
            src/client.cpp
			src/httprpc.cpp
			)


ADD_LIBRARY(rpc ${rpc_src})

target_link_libraries(rpc http)

