cmake_minimum_required(VERSION 2.6)
file(GLOB SOURCES *.cpp *.h)
add_library(CoreToolkit ${SOURCES})
if(UNIX)
	add_definitions(-D_FILE_OFFSET_BITS=64)
	if(CMAKE_SYSTEM_NAME STREQUAL "SunOS")
		target_link_libraries(CoreToolkit pthread nsl socket)
	else(CMAKE_SYSTEM_NAME STREQUAL "SunOS")
		target_link_libraries(CoreToolkit pthread)
	endif(CMAKE_SYSTEM_NAME STREQUAL "SunOS")
else(UNIX)
	target_link_libraries(CoreToolkit ws2_32)
endif(UNIX)
