set(XENO_EXAMPLES_POSIX bufp-label
bufp-readwrite
can-rtt
eth_p_all
iddp-label
xddp-label
xddp-stream)
# altency needs kernel-headers
set(XENO_EXAMPLES_LINK_FLAGS ${Xenomai_POSIX_LDFLAGS} ${Xenomai_POSIX_LIBRARY_DIRS})


foreach(xeno_app ${XENO_EXAMPLES_POSIX})
        message(STATUS "Working with ${xeno_app}")
        add_executable(${xeno_app} ${xeno_app}.c)
        #target_compile_definitions(${xeno_app} PRIVATE         ${Xenomai_POSIX_DEFINITIONS})
        target_include_directories(${xeno_app} PUBLIC 
                        ${Xenomai_POSIX_INCLUDE_DIRS} 
                        ${KERNELHEADERS_DIR})
        target_link_libraries(${xeno_app} ${Xenomai_POSIX_DL_FLAGS})
        set_target_properties(${xeno_app} PROPERTIES
                           COMPILE_FLAGS ${Xenomai_POSIX_DEFINITIONS})
endforeach(xeno_app ${XENO_EXAMPLES_POSIX})
