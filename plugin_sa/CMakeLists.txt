cmake_minimum_required(VERSION 3.18)

project("plugin-sa-sdk")

file(GLOB _PLUGIN_SA_SDK_SOURCES
  "${CMAKE_CURRENT_SOURCE_DIR}/game_sa/*.cpp"
  "${CMAKE_CURRENT_SOURCE_DIR}/game_sa/**/*.cpp"
  "${PLUGIN_SDK_ROOT}/shared/*.cpp"
  "${PLUGIN_SDK_ROOT}/shared/**/*.cpp"
  "${PLUGIN_SDK_ROOT}/shared/plugin.rc"
  "${PLUGIN_SDK_ROOT}/safetyhook/*.cpp"
  "${PLUGIN_SDK_ROOT}/safetyhook/*.c"
  "${PLUGIN_SDK_ROOT}/hooking/*.cpp"
)

add_library(plugin-sa-sdk STATIC ${_PLUGIN_SA_SDK_SOURCES})

target_include_directories(
  plugin-sa-sdk PUBLIC
  "${CMAKE_CURRENT_SOURCE_DIR}"
  "${CMAKE_CURRENT_SOURCE_DIR}/game_sa"
  "${PLUGIN_SDK_ROOT}/shared"
  "${PLUGIN_SDK_ROOT}/shared/bass/"
  "${PLUGIN_SDK_ROOT}/shared/comp/"
  "${PLUGIN_SDK_ROOT}/shared/dxsdk/"
  "${PLUGIN_SDK_ROOT}/shared/extender/"
  "${PLUGIN_SDK_ROOT}/shared/extensions/"
  "${PLUGIN_SDK_ROOT}/shared/game/"
  "${PLUGIN_SDK_ROOT}/shared/rwd3d9/"
  "${PLUGIN_SDK_ROOT}/safetyhook/"
  "${PLUGIN_SDK_ROOT}/hooking/"
  "${PLUGIN_SDK_ROOT}/injector/"
)

target_compile_definitions(
  plugin-sa-sdk PUBLIC
  _CRT_SECURE_NO_WARNINGS
  GTASA=1
  RW=1
)

set_target_properties(
  plugin-sa-sdk PROPERTIES
  CXX_STANDARD 23
)
