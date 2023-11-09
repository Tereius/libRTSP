include_directories("include" "../groupsock/include")

set(src_files
        HashTable.cpp
        strDup.cpp
        UsageEnvironment.cpp
)

set(public_header_files
        include/Boolean.hh
        include/HashTable.hh
        include/strDup.hh
        include/UsageEnvironment.hh
        include/UsageEnvironment_version.hh
)

add_library(UsageEnvironment STATIC ${src_files} ${public_header_files})
set_target_properties(UsageEnvironment PROPERTIES PUBLIC_HEADER "${public_header_files}")
install(TARGETS UsageEnvironment EXPORT UsageEnvironmentTargets RUNTIME DESTINATION bin ARCHIVE DESTINATION lib LIBRARY DESTINATION lib PUBLIC_HEADER DESTINATION include)
install(EXPORT UsageEnvironmentTargets DESTINATION cmake)
