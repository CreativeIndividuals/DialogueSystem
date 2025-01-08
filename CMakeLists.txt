cmake_minimum_required(VERSION 3.28)
project(DialogueSystem)

set(CMAKE_CXX_STANDARD 17)

if (CMAKE_BUILD_TYPE STREQUAL "Debug")
    add_compile_definitions(DEBUG_BUILD)
elseif (CMAKE_BUILD_TYPE STREQUAL "Release")
    add_compile_definitions(RELEASE_BUILD)
endif ()

add_subdirectory(src bin)

target_include_directories(${PROJECT_NAME} PRIVATE include)

set(LIBRARIES
        glad
        glfw
        imgui
)

include(libs/Libraries.cmake)
build_libraries(${PROJECT_NAME} "${PROJECT_SOURCE_DIR}" "${LIBRARIES}")

target_link_options(${PROJECT_NAME} PRIVATE -static)
