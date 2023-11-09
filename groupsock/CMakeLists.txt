include_directories("include" "../UsageEnvironment/include")

set(src_files
    GroupEId.cpp
    Groupsock.cpp
    GroupsockHelper.cpp
    inet.c
    IOHandlers.cpp
    NetAddress.cpp
    NetInterface.cpp
)

set(public_header_files
    include/GroupEId.hh
    include/groupsock_version.hh
    include/Groupsock.hh
    include/GroupsockHelper.hh
    include/IOHandlers.hh
    include/NetAddress.hh
    include/NetCommon.h
    include/NetInterface.hh
)

add_library(groupsock STATIC ${src_files} ${public_header_files})
set_target_properties(groupsock PROPERTIES PUBLIC_HEADER "${public_header_files}")
if(UNIX)
    target_compile_definitions(groupsock PUBLIC SOCKLEN_T=socklen_t)
endif ()
install(TARGETS groupsock EXPORT groupsockTargets RUNTIME DESTINATION bin ARCHIVE DESTINATION lib LIBRARY DESTINATION lib PUBLIC_HEADER DESTINATION include)
install(EXPORT groupsockTargets DESTINATION cmake)
