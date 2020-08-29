
add_executable(intersect_triangles_test.bin intersect_triangles_test.cpp)
target_link_libraries(intersect_triangles_test.bin gtest_main)
add_executable(static_vec_traits_test.bin static_vec_traits_test.cpp)
target_link_libraries(static_vec_traits_test.bin gtest_main)

add_executable(loadPLYMeshTest.bin loadPLYMeshTest.cpp plyfile.c)
target_link_libraries(loadPLYMeshTest.bin gtest_main)

add_executable(ManagerTest.bin ManagerTest.cu ManagerInst.cu createOBBTreePQPInst.cpp)
target_link_libraries(ManagerTest.bin gtest)
target_link_libraries(ManagerTest.bin PQP)

add_executable(ManagerExtendedTest.bin ManagerExtendedTest.cpp ManagerInst.cu createOBBTreePQPInst.cpp plyfile.c test_data_loader/test_data_loader.cpp)
target_link_libraries(ManagerExtendedTest.bin gtest)
target_link_libraries(ManagerExtendedTest.bin PQP)
target_compile_options(ManagerExtendedTest.bin PRIVATE $<$<COMPILE_LANGUAGE:CUDA>:-arch=sm_30>)

add_test(NAME intersect_triangles_test COMMAND intersect_triangles_test.bin)
add_test(NAME static_vec_traits_test COMMAND static_vec_traits_test.bin)

add_test(NAME loadPLYMeshTest COMMAND loadPLYMeshTest.bin)

add_test(NAME ManagerTest COMMAND ManagerTest.bin)