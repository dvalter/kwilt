configure_file(config-kwilt.h.in ${CMAKE_CURRENT_BINARY_DIR}/config-kwilt.h)

add_executable(kwilt)

target_sources(kwilt PRIVATE
    config/appearancesettings.cpp
    config/appearancesettings.h
    config/skinlistdelegate.cpp
    config/skinlistdelegate.h
    config/windowsettings.cpp
    config/windowsettings.h
    firstrundialog.cpp
    firstrundialog.h
    main.cpp
    mainwindow.cpp
    mainwindow.h
    session.cpp
    session.h
    sessionstack.cpp
    sessionstack.h
    skin.cpp
    skin.h
    splitter.cpp
    splitter.h
    tabbar.cpp
    tabbar.h
    terminal.cpp
    terminal.h
    titlebar.cpp
    titlebar.h
    visualeventoverlay.cpp
    visualeventoverlay.h
    outputorderwatcher.cpp
)

ki18n_wrap_ui(kwilt
    firstrundialog.ui
    config/windowsettings.ui
    config/behaviorsettings.ui
    config/appearancesettings.ui
)

if (Qt6_VERSION VERSION_GREATER_EQUAL "6.8.0")
    set(private_code_option  "PRIVATE_CODE")
endif()
qt6_generate_wayland_protocol_client_sources(kwilt
    ${private_code_option}
    FILES
        ${PLASMA_WAYLAND_PROTOCOLS_DIR}/kde-output-order-v1.xml
)

kconfig_add_kcfg_files(kwilt config/settings.kcfgc)

file(GLOB ICONS_SRCS "${CMAKE_CURRENT_SOURCE_DIR}/../data/icons/*-apps-kwilt.png")
ecm_add_app_icon(kwilt_SRCS ICONS ${ICONS_SRCS})


target_link_libraries(kwilt
    Qt::Widgets
    KF6::Archive
    KF6::ConfigGui
    KF6::CoreAddons
    KF6::Crash
    KF6::DBusAddons
    KF6::GlobalAccel
    KF6::I18n
    KF6::IconThemes
    KF6::KIOCore
    KF6::NewStuffWidgets
    KF6::Notifications
    KF6::NotifyConfig
    KF6::Parts
    KF6::WidgetsAddons
    KF6::WindowSystem
    KF6::StatusNotifierItem
    KF6::ColorScheme
    Wayland::Client
    Qt::WaylandClient
)

if(HAVE_X11)
    if(TARGET Qt6::Gui)
        target_link_libraries(kwilt Qt6::GuiPrivate XCB::RANDR XCB::UTIL) # qtx11extras_p.h
    endif()
endif()

if(KWayland_FOUND)
  target_link_libraries(kwilt Plasma::KWaylandClient)
endif()

install(TARGETS kwilt ${KDE_INSTALL_TARGETS_DEFAULT_ARGS})

install(FILES kwilt.knsrc DESTINATION ${KDE_INSTALL_KNSRCDIR})

install(FILES config/kwilt.kcfg DESTINATION ${KDE_INSTALL_KCFGDIR})
