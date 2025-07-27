cmake_minimum_required(VERSION 3.10)
project(Block_Engine)

# Use C++17
set(CMAKE_CXX_STANDARD 17)

# Set the external include and lib directories
include_directories("C:/Program Files/JetBrains/CLion 2024.3/bin/mingw/include")
include_directories("${PROJECT_SOURCE_DIR}/headers")
link_directories("C:/Program Files/lib")  # Change if GLFW/glad libs are somewhere else
if (WIN32)
    set(CMAKE_WIN32_EXECUTABLE ON)
endif()
# ImGui file paths (manually specified from external include dir)
set(IMGUI_BASE "C:/Program Files/JetBrains/CLion 2024.3/bin/mingw/include")
set(IMGUI_SOURCES
        "${IMGUI_BASE}/imgui//imgui.cpp"
        "${IMGUI_BASE}/imgui/imgui_demo.cpp"
        "${IMGUI_BASE}/imgui/imgui_draw.cpp"
        "${IMGUI_BASE}/imgui/imgui_tables.cpp"
        "${IMGUI_BASE}/imgui/imgui_widgets.cpp"
        "${IMGUI_BASE}/backends/imgui_impl_glfw.cpp"
        "${IMGUI_BASE}/backends/imgui_impl_opengl3.cpp"
)

# Add executable
add_executable(Block_Engine
        src/main.cpp
        src/glad.c
        ${IMGUI_SOURCES}
)

# Link everything
target_link_libraries(Block_Engine
        ws2_32
        dxgi
        glfw3
        kernel32
        user32
        gdi32
        winspool
        shell32
        ole32
        oleaut32
        uuid
        comdlg32
        advapi32
)
