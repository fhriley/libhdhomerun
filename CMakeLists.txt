cmake_minimum_required(VERSION 2.8.6)
project(hdhomerun)

set(CMAKE_THREAD_PREFER_PTHREAD ON)
find_package (Threads REQUIRED)

set(CMAKE_C_FLAGS "-O2 -Wall -Wextra -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wpointer-arith -Wno-unused-parameter")

set(hdhomerun_SOURCES hdhomerun_channels.c
					 hdhomerun_channelscan.c
					 hdhomerun_control.c
					 hdhomerun_debug.c
					 hdhomerun_device.c
					 hdhomerun_device_selector.c
					 hdhomerun_discover.c
					 hdhomerun_os_posix.c
					 hdhomerun_pkt.c
					 hdhomerun_sock_posix.c
					 hdhomerun_video.c)

add_library(hdhomerun STATIC ${hdhomerun_SOURCES})
target_link_libraries(hdhomerun ${CMAKE_THREAD_LIBS_INIT})

file(GLOB HEADERS "*.h")
install(FILES ${HEADERS} DESTINATION include)
install(TARGETS hdhomerun ARCHIVE DESTINATION lib) 
