add_definitions(-DTRANSLATION_DOMAIN="gwenview")

include_directories(
    ${CMAKE_CURRENT_SOURCE_DIR}/..
    )

set(gvpart_SRCS
    gvbrowserextension.cpp
    gvpart.cpp
    gvbrowserextension.h
    gvpart.h
    gvpart.qrc
    )

add_library(gvpart MODULE ${gvpart_SRCS})

target_link_libraries(gvpart KF5::Parts gwenviewlib)

configure_file(gvpart.desktop.cmake ${CMAKE_CURRENT_BINARY_DIR}/gvpart.desktop)
kcoreaddons_desktop_to_json(gvpart ${CMAKE_CURRENT_BINARY_DIR}/gvpart.desktop)

install(TARGETS gvpart DESTINATION ${KDE_INSTALL_PLUGINDIR}/kf${QT_MAJOR_VERSION}/parts)
install(FILES ${CMAKE_CURRENT_BINARY_DIR}/gvpart.desktop DESTINATION ${KDE_INSTALL_KSERVICESDIR})
