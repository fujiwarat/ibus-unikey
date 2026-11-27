find_package(PkgConfig REQUIRED)
pkg_check_modules(GTK3 REQUIRED IMPORTED_TARGET gtk+-3.0)

add_executable(ibus-setup-unikey
    main.cpp
    signal_handlers.cpp
    macro_utils.cpp
)
target_link_libraries(ibus-setup-unikey PRIVATE
    ukengine
    unikey-config
    PkgConfig::GTK3
)

install(TARGETS ibus-setup-unikey DESTINATION "${LIBEXECDIR}")
install(FILES ibus-unikey.ui DESTINATION "${PKGDATADIR}/ui")
