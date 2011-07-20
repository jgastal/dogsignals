set(CMAKE_C_COMPILER clang)
set(CMAKE_CXX_COMPILER clang++)

project(DogSignals)
set(PROJECT_VERSION 0.1)
cmake_minimum_required(VERSION 2.6)

set(SOURCES
        signal.hpp
        slot.hpp)

add_definitions(-Wno-c++0x-extensions)

add_library(signal SHARED ${SOURCES})
set_target_properties(json PROPERTIES OUTPUT_NAME ${PROJECT_NAME})
set_target_properties(json PROPERTIES VERSION ${PROJECT_VERSION})

configure_file(pkgconfig ${CMAKE_CURRENT_BINARY_DIR}/${PROJECT_NAME}.pc @ONLY)
install(FILES signal.h slot.h DESTINATION include/PulpJSON CONFIGURATIONS Release)
install(FILES ${CMAKE_CURRENT_BINARY_DIR}/${PROJECT_NAME}.pc DESTINATION lib/pkgconfig/ CONFIGURATIONS Release)

configure_file(Doxyfile .)
add_custom_target(doc doxygen)

