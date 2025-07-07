cmake_minimum_required(VERSION 3.15)

project(test)

message(STATUS "Compiling shader.vert...")

message(STATUS $ENV{VULKAN_SDK}/bin/glslc)

execute_process(COMMAND
  $ENV{VULKAN_SDK}/bin/glslang
  ${CMAKE_CURRENT_SOURCE_DIR}/shaders/shader.vert
  -o ${CMAKE_CURRENT_SOURCE_DIR}/shaders/shader.vert.spv
  RESULT_VARIABLE result
)
if(NOT result EQUAL "0")
    message( FATAL_ERROR "Failed to compile shader.vert")
endif()
