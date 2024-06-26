﻿# CMakeList.txt : CMake project for CMake-CPP-Things, include source and define
# project specific logic here.
#
cmake_minimum_required (VERSION 3.8)

# Enable Hot Reload for MSVC compilers if supported.
if (POLICY CMP0141)
  cmake_policy(SET CMP0141 NEW)
  set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")
endif()

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

SET(QTCP_PROJECT_DIR ${PROJECT_SOURCE_DIR})

project ("CPP-Datastructures" VERSION 1.0)

# Add source to this project's executable.
add_executable (CPP-Datastructures "main/main.cpp")
target_include_directories(CPP-Datastructures PUBLIC "${PROJECT_BINARY_DIR}")

# Test binaries
add_executable (ltest "tests/List/ltest.cpp")
target_include_directories(CPP-Datastructures PUBLIC "${PROJECT_BINARY_DIR}")
add_executable(ltest2 "tests/List/ltest2.cpp")
target_include_directories(CPP-Datastructures PUBLIC "${PROJECT_BINARY_DIR}")
add_executable(stacktest "tests/Stack/stacktest.cpp")
target_include_directories(CPP-Datastructures PUBLIC "${PROJECT_BINARY_DIR}")
add_executable(sltest "tests/LinkedLists/sltest.cpp")
target_include_directories(CPP-Datastructures PUBLIC "${PROJECT_BINARY_DIR}")
add_executable(dltest "tests/LinkedLists/dltest.cpp")

# Enable testing
enable_testing()

# Add tests
add_test(NAME ltest COMMAND ltest)
add_test(NAME ltest2 COMMAND ltest2)
add_test(NAME stacktest COMMAND stacktest)
add_test(NAME sltest COMMAND sltest)
add_test(NAME dltest COMMAND dltest)



# TODO: Add tests and install targets if needed.
