cmake_minimum_required(VERSION 3.0.0)
project(app2 VERSION 0.1.0)


include(CTest)
enable_testing()

SET(XYZ_NAME "l2")

include(FetchContent)
FetchContent_Declare(
    xyz2
    GIT_REPOSITORY https://github.com/mariuszmaximus/xyz.git
    GIT_TAG 9ca3db6f67b18195c78224d69ccca136ed6d5a72
)
FetchContent_Populate(xyz2)
add_subdirectory(${xyz2_SOURCE_DIR} ${xyz2_BINARY_DIR})


add_executable(app2 main.cpp)
target_link_libraries(app2  ${XYZ_NAME}) 

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)
