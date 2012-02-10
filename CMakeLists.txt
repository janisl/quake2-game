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

add_subdirectory(baseq2)
add_subdirectory(ctf)
add_subdirectory(rogue)
add_subdirectory(xatrix)
