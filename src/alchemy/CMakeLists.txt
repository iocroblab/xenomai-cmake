
set(XENO_EXAMPLES_ALCHEMY cross-link)
# altency needs kernel-headers
set(XENO_EXAMPLES_LINK_FLAGS ${Xenomai_ALCHEMY_LDFLAGS} ${Xenomai_ALCHEMY_LIBRARY_DIRS})


foreach(xeno_app ${XENO_EXAMPLES_ALCHEMY})
	message(STATUS "Working with ${xeno_app}")
	add_executable(${xeno_app} ${xeno_app}.c)
	#target_compile_definitions(${xeno_app} PRIVATE 	${Xenomai_ALCHEMY_DEFINITIONS})
	target_include_directories(${xeno_app} PUBLIC 
			${Xenomai_ALCHEMY_INCLUDE_DIRS} 
			${KERNELHEADERS_DIR})
	target_link_libraries(${xeno_app} ${Xenomai_ALCHEMY_DL_FLAGS})
	set_target_properties(${xeno_app} PROPERTIES
			   COMPILE_FLAGS ${Xenomai_ALCHEMY_DEFINITIONS})
endforeach(xeno_app ${XENO_EXAMPLES_ALCHEMY})