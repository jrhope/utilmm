set(SOURCES_UNIX_ONLY
    test_pkgconfig.cc
    test_process.cc
    test_shellexpand.cc
    test_system.cc)

set(SOURCES
    test_configfile.cc
    test_misc.cc
    testsuite.cc
    test_undirected_graph.cc)

if (NOT WIN32 AND NOT VXWORKS)
  set(SOURCES ${SOURCES} ${SOURCES_UNIX_ONLY})
endif (NOT WIN32 AND NOT VXWORKS)

ADD_EXECUTABLE(utilmm_testsuite ${SOURCES})

TARGET_LINK_LIBRARIES(utilmm_testsuite utilmm
    ${Boost_UNIT_TEST_FRAMEWORK_LIBRARIES} ${Boost_SYSTEM_LIBRARIES})
ADD_TEST(Suite ${CMAKE_CURRENT_BINARY_DIR}/utilmm_testsuite --catch_system_errors=no)

