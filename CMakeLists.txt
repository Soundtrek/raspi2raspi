cmake_minimum_required(VERSION 2.6)

set(CMAKE_BUILD_TYPE Release)
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wall")

include_directories(/opt/vc/include)
include_directories(/opt/vc/include/interface/vcos/pthreads)
include_directories(/opt/vc/include/interface/vmcs_host)
include_directories(/opt/vc/include/interface/vmcs_host/linux)

link_directories(/opt/vc/lib)

add_executable(raspi2raspi raspi2raspi.c syslogUtilities.c)

target_link_libraries(raspi2raspi bcm_host bsd)

set_property(TARGET raspi2raspi PROPERTY SKIP_BUILD_RPATH TRUE)
install (TARGETS raspi2raspi RUNTIME DESTINATION bin)
