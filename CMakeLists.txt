cmake_minimum_required(VERSION 3.2)


set(project_name starter_project)
project(${project_name})

# add_definitions(-DDEBUG)
file(GLOB_RECURSE src_files "src/*.rc" "src/*.cpp" "src/*.c" "src/*.h")

add_executable( ${project_name} #SHARED
    ${src_files}
)


# GLFW
add_subdirectory(vendor/glfw)

include_directories(vendor/glfw/include)
target_link_libraries(${project_name} glfw ${GLFW_LIBRARIES})

# GLAD
add_subdirectory(vendor/glad)

include_directories(vendor/glad/include)
target_link_libraries(${project_name} glad ${GLAD_LIBRARIES})

#ImGUI
add_library(imgui STATIC
	vendor/imgui/backends/imgui_impl_opengl3.cpp
	vendor/imgui/backends/imgui_impl_glfw.cpp
	vendor/imgui/imgui.cpp
	vendor/imgui/imgui_demo.cpp
	vendor/imgui/imgui_draw.cpp
	vendor/imgui/imgui_widgets.cpp
	vendor/imgui/imgui_tables.cpp    
)
include_directories(vendor/imgui)
target_link_libraries(${project_name} imgui ${IMGUI_LIBRARIES})

#GLM
include_directories(vendor/glm)
