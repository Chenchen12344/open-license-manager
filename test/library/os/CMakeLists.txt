add_executable( test_network
 network_test.cpp
)

target_link_libraries( test_network
 licensecc_static
 Boost::unit_test_framework 
 Boost::filesystem
 Boost::system
)

ADD_TEST(NAME test_network COMMAND test_network)

add_executable( test_execution_environment
 execution_environment_test.cpp
)

target_link_libraries( test_execution_environment
 licensecc_static
 Boost::unit_test_framework 
 Boost::filesystem
 Boost::system
)

ADD_TEST(NAME test_execution_environment COMMAND test_execution_environment)
if(CODE_COVERAGE AND UNIX)
	target_compile_options(test_network PUBLIC -O0 -g --coverage)
	target_compile_options(test_execution_environment PUBLIC -O0 -g --coverage)
endif(CODE_COVERAGE AND UNIX)
