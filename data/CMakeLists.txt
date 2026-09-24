add_subdirectory(icons)
add_subdirectory(skins)

ecm_generate_dbus_service_file(
    NAME org.kde.kwilt
    EXECUTABLE ${KDE_INSTALL_FULL_BINDIR}/kwilt
    DESTINATION ${KDE_INSTALL_DBUSSERVICEDIR}
)

install(FILES org.kde.kwilt.desktop DESTINATION ${KDE_INSTALL_APPDIR})
install(FILES org.kde.kwilt.appdata.xml DESTINATION  ${KDE_INSTALL_METAINFODIR})
install(FILES kwilt.notifyrc DESTINATION ${KDE_INSTALL_KNOTIFYRCDIR})
