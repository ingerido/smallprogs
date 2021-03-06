
cmake_minimum_required(VERSION 2.8 FATAL_ERROR)

project(T C CXX)

set(CMAKE_VERBOSE_MAKEFILE on)

set(CMAKE_COLOR_MAKEFILE)

set(CXX_STANDARD c++14)

set(CMAKE_BUILD_TYPE Release)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=${CXX_STANDARD} -Wnon-virtual-dtor -Woverloaded-virtual -DBOOST_LOG_DYN_LINK")

# these below apply to C and C++ files
add_compile_options(
  -Wall
  -Wextra
  -Wstrict-aliasing
  -Wno-unused-parameter
  -Wno-missing-field-initializers
  -Wchar-subscripts
  -Wpointer-arith
  -Wformat
  -Wformat-security
  -Werror=format-security
  -fstack-protector-all
  -fPIE
  -fpie
  -fPIC
  -fpic
  -pipe
  -fdata-sections
  -ffunction-sections
)

ADD_EXECUTABLE(set_tester
    set.cpp
    set_test.cpp
    test_main.cpp)

TARGET_LINK_LIBRARIES(set_tester
    gtest
    pthread
    rt)

ADD_EXECUTABLE(thrset_test
	set.cpp
    thrset_test.cpp
	)

TARGET_LINK_LIBRARIES(thrset_test
    pthread
    )

ADD_EXECUTABLE(skiptest
    skiptest.cpp
	)

TARGET_LINK_LIBRARIES(skiptest
	folly
	glog
    pthread
    )

ADD_EXECUTABLE(stack_test
    stack_test.cpp
	)

TARGET_LINK_LIBRARIES(stack_test
    pthread
    )

ADD_EXECUTABLE(queue_test
    queue_test.cpp
	)

TARGET_LINK_LIBRARIES(queue_test
    pthread
    )

ADD_EXECUTABLE(spsc_queue_test
    spsc_queue_test.cpp
	)

TARGET_LINK_LIBRARIES(spsc_queue_test
    pthread
    )
