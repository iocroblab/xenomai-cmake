set(XENO_POSIX_SRC cyclictest.c error.c rt-utils.c)
set(XENO_POSIX_HDRS rt-utils.h 	error.h rt_numa.h rt-sched.h)

set(VERSION_STRING 0.92)
add_definitions(-DVERSION_STRING=${VERSION_STRING})

message(STATUS "Working with ${xeno_app}")
add_executable(cyclictest ${XENO_POSIX_SRC})
target_include_directories(cyclictest PUBLIC ${Xenomai_POSIX_INCLUDE_DIRS})
target_link_libraries(cyclictest ${Xenomai_POSIX_DL_FLAGS})
set_target_properties(cyclictest PROPERTIES
                           COMPILE_FLAGS ${Xenomai_POSIX_DEFINITIONS})
