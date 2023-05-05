
set(sources
        "serial.cc"
        )
if (WIN32)

    list(APPEND sources
            "impl/win.cc"
            "impl/list_ports/list_ports_win.cc")
else ()
    list(APPEND sources
            "impl/unix.cc")
    if (APPLE)
        list(APPEND sources
                "impl/list_ports/list_ports_osx.cc")
    else ()
        list(APPEND sources
                "impl/list_ports/list_ports_linux.cc")
    endif ()

endif ()

add_library(serial ${sources})
target_include_directories(serial PUBLIC "${PROJECT_SOURCE_DIR}/include")
if (WIN32)
    target_link_libraries(serial PRIVATE SetupApi)
endif ()
