
set(XENO_EXAMPLES_NATIVE sigdebug rtprint trivial-periodic)
set(XENO_EXAMPLES_LINK_FLAGS ${Xenomai_NATIVE_LDFLAGS} ${Xenomai_NATIVE_LIBRARY_DIRS})

foreach(xeno_app ${XENO_EXAMPLES_NATIVE})
	message(STATUS "Working with ${xeno_app}")
	add_executable(${xeno_app} ${xeno_app}.c)
	target_include_directories(${xeno_app} PUBLIC ${Xenomai_NATIVE_INCLUDE_DIRS})
	target_link_libraries(${xeno_app} ${Xenomai_NATIVE_DL_FLAGS})
	set_target_properties(${xeno_app} PROPERTIES
			   COMPILE_FLAGS ${Xenomai_NATIVE_DEFINITIONS})
endforeach(xeno_app ${XENO_EXAMPLES_NATIVE})