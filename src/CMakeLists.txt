
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
target_include_directories(serial
        PUBLIC
        "$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/../include>"
        "$<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>"
        )
if (WIN32)
    target_link_libraries(serial PRIVATE SetupApi)
elseif (APPLE)
    find_library(IOKIT_LIBRARY IOKit)
    find_library(FOUNDATION_LIBRARY Foundation)

    target_link_libraries(serial PRIVATE ${FOUNDATION_LIBRARY} ${IOKIT_LIBRARY})
else ()
    target_link_libraries(serial PRIVATE rt pthread)
endif ()
