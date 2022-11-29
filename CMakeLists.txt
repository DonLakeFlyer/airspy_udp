cmake_minimum_required(VERSION 3.10.2)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_BUILD_TYPE Debug)

project(airspy_rx_udp)

include_directories(airspy_rx_udp
    /usr/include/libairspy)

add_executable(airspy_rx_udp 
    airspy_rx_udp.c)

find_package(MAVSDK REQUIRED)

target_link_libraries(airspy_rx_udp
    airspy
    -lm
)

add_compile_options(airspy_rx_udp PRIVATE -g)
add_link_options(airspy_rx_udp PRIVATE -g)

add_compile_options(airspy_rx_udp PRIVATE -Wall -Wextra)

install(TARGETS airspy_rx_udp RUNTIME DESTINATION bin)

