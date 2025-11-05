# west workspace path
set(WORKSPACE_DIR "${CMAKE_CURRENT_LIST_DIR}")

# libraries fetched by https://github.com/cpm-cmake/CPM.cmake are moved here
set(CPM_SOURCE_CACHE "${WORKSPACE_DIR}/cpm")

include(FetchContent)
function(fetch_from_workspace name)
    set(options)
    set(oneValueArgs SOURCE_DIR)
    set(multiValueArgs)
    cmake_parse_arguments(ARG "${options}" "${oneValueArgs}" "${multiValueArgs}" ${ARGN})

    if(NOT ARG_SOURCE_DIR)
        set(ARG_SOURCE_DIR "${WORKSPACE_DIR}/${name}")
    endif()

    FetchContent_Declare(
        ${name}
        SOURCE_DIR ${ARG_SOURCE_DIR}
    )
    FetchContent_MakeAvailable(${name})
endfunction()
