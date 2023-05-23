cmake_minimum_required(VERSION 3.0)

if(CMAKE_SYSTEM_NAME STREQUAL "Linux")
    set(SYSTEM_FILES linux.c linux_termios.c linux_termios.h)
endif()

if(CMAKE_SYSTEM_NAME STREQUAL "Darwin")
    set(SYSTEM_FILES macosx.c)
endif()

if(CMAKE_SYSTEM_NAME STREQUAL "Windows")
    set(SYSTEM_FILES linux.c linux_termios.c linux_termios.h)
endif()

if(CMAKE_SYSTEM_NAME STREQUAL "FreeBSD")
    set(SYSTEM_FILES freebsd.c)
endif()

add_library(
    sigrok_serialport STATIC
    libserialport_internal.h
    ${SYSTEM_FILES}
    serialport.c
    timing.c
    libserialport.h
)
target_include_directories(sigrok_serialport ${CMAKE_CURRENT_SOURCE_DIR})