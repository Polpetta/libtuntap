# libtuntap C++ binding CMakeLists.txt
# ====================================

set(CMAKE_CXX_STANDARD 11)

include_directories(
    ${CMAKE_CURRENT_SOURCE_DIR}/bindings/cpp
)

add_library(tuntap++ SHARED
    ${CMAKE_CURRENT_SOURCE_DIR}/bindings/cpp/tuntap++.cc
    ${CMAKE_CURRENT_SOURCE_DIR}/bindings/cpp/tuntap++.hh
)
set_target_properties(tuntap++ PROPERTIES VERSION 2.1)

add_library(tuntap++-static STATIC
        ${CMAKE_CURRENT_SOURCE_DIR}/bindings/cpp/tuntap++.cc
        ${CMAKE_CURRENT_SOURCE_DIR}/bindings/cpp/tuntap++.hh
)
set_target_properties(tuntap++-static PROPERTIES OUTPUT_NAME "tuntap++")

target_link_libraries(tuntap++ tuntap)

target_link_libraries(tuntap++-static tuntap)

install(TARGETS tuntap++ DESTINATION lib)
install(FILES ${CMAKE_CURRENT_SOURCE_DIR}/bindings/cpp/tuntap++.hh DESTINATION include)
install(TARGETS tuntap++-static DESTINATION lib)
