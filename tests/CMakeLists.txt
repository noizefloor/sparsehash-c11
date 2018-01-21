
find_package(Threads)

add_executable(sparsehash_unittests
    testmain.cc
    sparsetable_unittests.cc
    simple_unittests.cc
    hashtable_unittests.cc
    hashtable_c11_unittests.cc
    fixture_unittests.cc
    allocator_unittests.cc)

target_include_directories(sparsehash_unittests PRIVATE ${CMAKE_CURRENT_SOURCE_DIR})

add_test(sparsehash_unittests sparsehash_unittests)

target_link_libraries(sparsehash_unittests
    PRIVATE
        gtest
        gmock
        sparsehash
        ${CMAKE_THREAD_LIBS_INIT})

add_executable(bench bench.cc)

target_link_libraries(bench
        sparsehash
        ${CMAKE_THREAD_LIBS_INIT})
