cmake_minimum_required(VERSION 3.29)

find_package(Vulkan REQUIRED)
project(VulkanTutorial LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 23)
file(GLOB_RECURSE MY_SOURCES CONFIGURE_DEPENDS "${CMAKE_CURRENT_SOURCE_DIR}/src/*.cpp")
file(GLOB_RECURSE MY_HEADERS CONFIGURE_DEPENDS "${CMAKE_CURRENT_SOURCE_DIR}/include/*.h")
file(GLOB_RECURSE MY_RESOURCES CONFIGURE_DEPENDS "${CMAKE_CURRENT_SOURCE_DIR}/resources/*")

add_executable(VulkanTutorial "${MY_SOURCES}" "${MY_HEADERS}" "${MY_RESOURCES}")
target_include_directories(VulkanTutorial PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/include/")
target_link_libraries(VulkanTutorial PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/thirdParty/libglfw3.a)
target_link_libraries(VulkanTutorial PRIVATE Vulkan::Vulkan)
target_compile_options(VulkanTutorial PRIVATE -Wall -Wextra -g)
