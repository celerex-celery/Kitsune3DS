add_executable(citra_meta
    citra.rc
    main.cpp
    precompiled_headers.h
)

set_target_properties(citra_meta PROPERTIES OUTPUT_NAME "kitsune3ds")

if (BSD STREQUAL "NetBSD")
    include(DisablePaxMprotect)
    disable_pax_mprotect(citra_meta)
endif()


if(CMAKE_HOST_SYSTEM_NAME STREQUAL "Linux" AND MINGW)
    # TODO: Do this for all executables, not just citra_meta
    # TODO: Don't hardcode MXE directory?
    set(dllwalker_command "${CMAKE_SOURCE_DIR}/externals/dllwalker/dllwalker.rb"
                          $<TARGET_FILE:citra_meta>
                          /opt/mxe/usr/x86_64-w64-mingw32.shared/bin/
                          /opt/mxe/usr/x86_64-w64-mingw32.shared/qt6/bin/
                          /opt/mxe/usr/x86_64-w64-mingw32.shared/x86_64-w64-mingw32/bin/)
    set(dll_list_filename "${CMAKE_CURRENT_BINARY_DIR}/required_dlls_list.txt")
    add_custom_command(TARGET citra_meta POST_BUILD
        COMMAND ${dllwalker_command} > ${dll_list_filename}
    )
    add_custom_command(TARGET citra_meta POST_BUILD
        COMMAND cat ${dll_list_filename} | xargs -I {} ${CMAKE_COMMAND} -E copy {} $<TARGET_FILE_DIR:citra_meta>
        COMMAND ${CMAKE_COMMAND} -E make_directory "$<TARGET_FILE_DIR:citra_meta>/plugins/"
        COMMAND ${CMAKE_COMMAND} -E copy_directory /opt/mxe/usr/x86_64-w64-mingw32.shared/qt6/plugins/ "$<TARGET_FILE_DIR:citra_meta>/plugins/"
        COMMAND_EXPAND_LISTS
        DEPENDS ${dll_list_filename}
    )
endif()

target_link_libraries(citra_meta PRIVATE citra_cli citra_common fmt)

if (ENABLE_QT)
    target_link_libraries(citra_meta PRIVATE citra_qt)
endif()

if (ENABLE_ROOM)
    target_link_libraries(citra_meta PRIVATE citra_room)
endif()

if (ENABLE_QT AND ENABLE_DISCORD_RPC)
    target_link_libraries(citra_meta PRIVATE discord-rpc)
endif()

if(WIN32)
    # compile as a win32 gui application instead of a console application
    if(MSVC)
        set_target_properties(citra_meta PROPERTIES LINK_FLAGS_RELEASE "/SUBSYSTEM:WINDOWS")
    elseif(MINGW)
        set_target_properties(citra_meta PROPERTIES LINK_FLAGS_RELEASE "-mwindows")
    endif()
endif()

if (CITRA_USE_PRECOMPILED_HEADERS)
    target_precompile_headers(citra_meta PRIVATE precompiled_headers.h)
endif()

# Bundle in-place on MSVC so dependencies can be resolved by builds.
if (ENABLE_QT AND MSVC)
    include(BundleTarget)
    qt_bundle_target_in_place(citra_meta)
endif()
