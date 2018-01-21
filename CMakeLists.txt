cmake_minimum_required(VERSION 3.5)

project (sparsehash)

option(SPARSEHASH_ENABLE_TESTING "Enable testing of the sparsehash library." ON)

add_library(sparsehash INTERFACE)

target_compile_features(sparsehash INTERFACE cxx_std_11)

target_include_directories(sparsehash
        INTERFACE
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/>
        $<INSTALL_INTERFACE:include/google/sparsehash>)

install(DIRECTORY sparsehash DESTINATION include/google)
install(TARGETS sparsehash EXPORT sparsehash-config DESTINATION sparsehash/include)
install(EXPORT sparsehash-config DESTINATION share/sparsehash/cmake)

if(SPARSEHASH_ENABLE_TESTING)
    include(googletest.cmake)
    enable_testing()
    add_subdirectory(tests)
endif()


