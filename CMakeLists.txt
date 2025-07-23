cmake_minimum_required(VERSION 3.12)
project(imgui LANGUAGES C CXX)

# Grab all ImGui sources in this folder
file(GLOB IMGUI_SOURCES
    "${CMAKE_CURRENT_SOURCE_DIR}/*.cpp"
)

# Build the static library
add_library(imgui STATIC ${IMGUI_SOURCES})

# Create the "imgui::imgui" alias so your top-level CMake can link to it
add_library(imgui::imgui ALIAS imgui)

# Public include directory
target_include_directories(imgui PUBLIC
    "${CMAKE_CURRENT_SOURCE_DIR}"
)

# If you want the header-only math operators baked in here instead of your node-editor
# wrapper, you can define this, but since you already define them in axNodeEditor, you
# can omit it here. Uncomment if you need ImGui’s own operators:
# target_compile_definitions(imgui PUBLIC IMGUI_DEFINE_MATH_OPERATORS)
