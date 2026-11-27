find_package(PkgConfig REQUIRED)
pkg_check_modules(IBUS REQUIRED IMPORTED_TARGET ibus-1.0>=1.5)

add_subdirectory(config)

add_executable(ibus-engine-unikey
    main.cpp
    engine.cpp
)
target_link_libraries(ibus-engine-unikey PRIVATE
    ukengine
    unikey-config
    PkgConfig::IBUS
)

configure_file(unikey.xml.in unikey.xml)

install(TARGETS ibus-engine-unikey DESTINATION "${LIBEXECDIR}")
install(FILES "${CMAKE_CURRENT_BINARY_DIR}/unikey.xml" DESTINATION "${CMAKE_INSTALL_FULL_DATADIR}/ibus/component")
