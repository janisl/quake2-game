project(quake2-game)

cmake_minimum_required(VERSION 2.6)
if(COMMAND cmake_policy)
	cmake_policy(SET CMP0003 NEW)
endif(COMMAND cmake_policy)

#
#  **** Check for size of void* (to detect 64 bit systems) ****
#

include(CheckTypeSize)
check_type_size(void*  SIZEOF_VOID_PTR)

if(${SIZEOF_VOID_PTR} MATCHES "^4$")
	set(ARCH i386)
else(${SIZEOF_VOID_PTR} MATCHES "^4$")
	set(ARCH x86_64)
endif(${SIZEOF_VOID_PTR} MATCHES "^4$")

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -fvisibility=hidden")
set(CMAKE_C_FLAGS_DEBUG "${CMAKE_C_FLAGS_DEBUG} -D_DEBUG")
set(CMAKE_C_FLAGS_RELEASE "${CMAKE_C_FLAGS_RELEASE} -m486 -O6 -ffast-math -funroll-loops -fomit-frame-pointer -fexpensive-optimizations -malign-loops=2 malign-jumps=2 -malign-functions=2")

set(LDFLAGS dl m)

add_subdirectory(baseq2)
add_subdirectory(ctf)
add_subdirectory(rogue)
add_subdirectory(xatrix)
