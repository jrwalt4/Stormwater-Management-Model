#
# CMakeLists.txt - CMake configuration file for swmm-solver/tests
#
# Created: Jul 7, 2020
#
# Author: Michael E. Tryby
#         US EPA ORD/CESER
#


#Prep ourselves for compiling with boost
include(../extern/boost.cmake)


add_subdirectory(outfile)
add_subdirectory(solver)


# ctest doesn't like tests added in subdirectories so adding them here
add_test(NAME test_lid
    COMMAND test_lid
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/solver/data
)

add_test(NAME test_output
    COMMAND test_output
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/outfile/data
)

add_test(NAME test_solver
    COMMAND test_solver
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/solver/data
)
