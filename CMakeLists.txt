
# DX11 DX12 VULKAN
set (IMGUI_BACKEND CACHE STRING "selected imgui backend")


if (${IMGUI_BACKEND} STREQUAL "DX12")
    message ("imgui backend : DX12")
    set (IMGUI_BACKEND_SOURCES
        backends/imgui_impl_dx12.h
        backends/imgui_impl_win32.h
        backends/imgui_impl_dx12.cpp
        backends/imgui_impl_win32.cpp)
elseif (${IMGUI_BACKEND} STREQUAL "DX11")
    message ("imgui backend : DX11")
    set (IMGUI_BACKEND_SOURCES
        backends/imgui_impl_dx11.h
        backends/imgui_impl_win32.h
        backends/imgui_impl_dx11.cpp
        backends/imgui_impl_win32.cpp)
elseif (${IMGUI_BACKEND} STREQUAL "VULKAN")
    set (IMGUI_BACKEND_SOURCES
        backends/imgui_impl_vulkan.h
        backends/imgui_impl_vulkan.cpp)
endif ()

set (IMGUI_HEADERS
    imgui.h
    imgui_internal.h
    imconfig.h
    imstb_rectpack.h
    imstb_textedit.h
    imstb_truetype.h)

set (IMGUI_SOURCES
    ${IMGUI_BACKEND_SOURCES}
    imgui.cpp
	imgui_demo.cpp
    imgui_draw.cpp
    imgui_tables.cpp
    imgui_widgets.cpp)


set (IMGUI ${IMGUI_SOURCES} ${IMGUI_HEADERS})

add_library (imgui ${IMGUI})

target_include_directories (imgui PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
