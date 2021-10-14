project(umm_malloc)
add_library(umm_malloc OBJECT)
add_library(umm_malloc::umm_malloc ALIAS umm_malloc)

target_sources(umm_malloc
    PRIVATE
        src/umm_info.c
        src/umm_integrity.c
        src/umm_malloc_cfg.h
        src/umm_malloc.c
        src/umm_poison.c
    PUBLIC
        src/umm_malloc.h
)

file(TOUCH ${CMAKE_CURRENT_BINARY_DIR}/umm_malloc_cfgport.h)

target_include_directories(
    umm_malloc
    PUBLIC
        "src"
    PRIVATE
        "${CMAKE_CURRENT_BINARY_DIR}"
)
