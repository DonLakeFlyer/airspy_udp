cmake_minimum_required(VERSION 3.10.2)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
SET(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} -pthread")

project(airspy_rx_udp)

set(INSTALL_DEFAULT_BINDIR "bin" CACHE STRING "Appended to CMAKE_INSTALL_PREFIX")
install(TARGETS airspy_rx_udp RUNTIME DESTINATION ${INSTALL_DEFAULT_BINDIR})

include_directories(airspy_rx_udp
    /usr/include/libairspy)

add_executable(airspy_rx_udp 
    airspy_rx.c)

find_package(MAVSDK REQUIRED)

target_link_libraries(airspy_rx_udp
    airspy
    -lm
)

add_compile_options(airspy_rx_udp PRIVATE -g)
add_link_options(airspy_rx_udp PRIVATE -g)

add_compile_options(airspy_rx_udp PRIVATE -Wall -Wextra)
