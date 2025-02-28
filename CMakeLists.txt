add_library(imgui STATIC
    # Backend files for WebGPU and GLFW:
    backends/imgui_impl_wgpu.h
    backends/imgui_impl_wgpu.cpp
    backends/imgui_impl_glfw.h
    backends/imgui_impl_glfw.cpp

    # Optional C++ utilities:
    misc/cpp/imgui_stdlib.h
    misc/cpp/imgui_stdlib.cpp

    # Core ImGui files:
    imconfig.h
    imgui.h
    imgui.cpp
    imgui_draw.cpp
    imgui_internal.h
    imgui_tables.cpp
    imgui_widgets.cpp
    imstb_rectpack.h
    imstb_textedit.h
    imstb_truetype.h
)

target_include_directories(imgui PUBLIC .)
target_link_libraries(imgui PUBLIC webgpu glfw)

if(NOT EMSCRIPTEN)
    target_compile_definitions(imgui PUBLIC IMGUI_IMPL_WEBGPU_BACKEND_WGPU)
endif()


