cmake_minimum_required(VERSION 3.0)

project (ForwardAD)
set(target ForwardAD)

set(FEMSOURCES
src/MainTest.cpp
)

set(FEMINCLUDES
include/Dual.hpp
include/debug.hpp
include/Tensor.hpp
)

include_directories(include) 

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O2 -pg -std=c++17 -march=native")

add_executable (ForwardAD ${FEMSOURCES} ${FEMINCLUDES})

# linking
#target_link_libraries(ForwardAD) 

# install
install(TARGETS ForwardAD DESTINATION ${CMAKE_INSTALL_PREFIX})

