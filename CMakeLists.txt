cmake_minimum_required(VERSION 3.20)

project(nothofagus_demo_project CXX)

# Setting up build options for GLFW
option(NOTHOFAGUS_INSTALL "Disabling installation of Nothofagus" OFF)
add_subdirectory("third_party/nothofagus")

message(NOTHOFAGUS_INCLUDE="${NOTHOFAGUS_INCLUDE}")

file(GLOB_RECURSE HEADERS "source/*.h" "include/*.h")

add_executable(nothofagus_demo
    "source/nothofagus_demo.cpp"
)
set_property(TARGET nothofagus_demo PROPERTY CXX_STANDARD 20)
target_include_directories(nothofagus_demo PRIVATE ${NOTHOFAGUS_INCLUDE})
target_link_libraries(nothofagus_demo PRIVATE nothofagus)