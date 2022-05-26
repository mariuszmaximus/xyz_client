cmake_minimum_required(VERSION 3.0.0)
project(app1 VERSION 0.1.0)

include(CTest)
enable_testing()


SET(XYZ_NAME "l1")

include(FetchContent)
FetchContent_Declare(
    xyz1
    GIT_REPOSITORY https://github.com/mariuszmaximus/xyz.git
    GIT_TAG 6f0ceeef58f068a17942c88c462e60d49679ac29
)
FetchContent_Populate(xyz1)
add_subdirectory(${xyz1_SOURCE_DIR} ${xyz1_BINARY_DIR})


add_executable(app1 main.cpp)
target_link_libraries(app1 ${XYZ_NAME}) 

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)
