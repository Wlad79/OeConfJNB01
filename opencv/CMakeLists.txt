# CMakeLists.txt
# https://opencvguide.readthedocs.io/en/latest/opencvcpp/basics.html
# https://stackoverflow.com/questions/44487053/set-pkg-config-path-in-cmake

cmake_minimum_required(VERSION 3.8)
project( HelloOpenCVExample )
find_package(PkgConfig REQUIRED)
# this looks for opencv.pc file and creates a new target
# IMPORTED_TARGET requires CMake >= 3.6.3
pkg_search_module(PKG_OPENCV REQUIRED IMPORTED_TARGET opencv4)
add_executable( HelloOpenCV HelloOpenCV.cpp )
target_include_directories(HelloOpenCV PUBLIC ${PKG_OPENCV_INCLUDE_DIRS})
target_link_libraries(HelloOpenCV PRIVATE PkgConfig::PKG_OPENCV)

#message(WARNING "`PkgConfig::PKG_OPENCV}`     `PkgConfig::PKG_OPENCV_LIBRARIES`")