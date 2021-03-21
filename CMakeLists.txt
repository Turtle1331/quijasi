cmake_minimum_required(VERSION 3.10)

project(Quijasi)



set(qjs_path "wasi-lab/qjs-wasi")
add_subdirectory(${qjs_path})

add_definitions(
    -D_GNU_SOURCE
    -DCONFIG_VERSION="2019-07-09"
)

set(qjs_sources
    ${qjs_path}/src/cutils.c
    ${qjs_path}/src/libregexp.c
    ${qjs_path}/src/libunicode.c
    ${qjs_path}/src/qjs.c
    ${qjs_path}/src/quickjs-libc.c
    ${qjs_path}/src/quickjs.c
    ${qjs_path}/src/repl.c
)

add_library(qjslib STATIC ${qjs_sources})

set(CMAKE_EXPORT_COMPILE_COMMANDS on)



add_subdirectory(wasm3)



add_executable(quijasi quijasi/main.c)
target_include_directories(quijasi PRIVATE ${qjs_path}/src)
target_link_libraries(quijasi m3 qjslib)
