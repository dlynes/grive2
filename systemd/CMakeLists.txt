SET(GRIVE_SYNC_SH_BINARY "${CMAKE_INSTALL_FULL_LIBEXECDIR}/grive/grive-sync.sh")

CONFIGURE_FILE(grive-changes@.service.in grive-changes@.service @ONLY)
CONFIGURE_FILE(grive-timer@.service.in grive-timer@.service @ONLY)

install(
  FILES
    grive@.service
    ${CMAKE_BINARY_DIR}/systemd/grive-changes@.service
    ${CMAKE_BINARY_DIR}/systemd/grive-timer@.service
  DESTINATION
    lib/systemd/user
)

install(
  FILES
    grive-timer@.timer
  DESTINATION
    lib/systemd/user
)

install(
  PROGRAMS
    grive-sync.sh
  DESTINATION
    ${CMAKE_INSTALL_FULL_LIBEXECDIR}/grive
)
