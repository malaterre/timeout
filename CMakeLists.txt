cmake_minimum_required(VERSION 2.8)
project(timeout NONE)
enable_testing()
# timeout
add_test(NAME dummy1 COMMAND sleep 10)
set_tests_properties(dummy1 PROPERTIES TIMEOUT 4)
add_test(NAME dummy2 COMMAND echo "not ok !")
set_tests_properties(dummy2 PROPERTIES DEPENDS dummy1)
set_tests_properties(dummy2 PROPERTIES WILL_FAIL 1)
# failed test:
add_test(NAME dummy3 COMMAND ls /urs)
add_test(NAME dummy4 COMMAND echo "not ok !")
set_tests_properties(dummy4 PROPERTIES DEPENDS dummy3)
set_tests_properties(dummy4 PROPERTIES WILL_FAIL 1)
