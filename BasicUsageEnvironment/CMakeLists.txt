include_directories("include" "../UsageEnvironment/include" "../groupsock/include")

set(src_files
        BasicHashTable.cpp
        BasicTaskScheduler.cpp
        BasicTaskScheduler0.cpp
        BasicUsageEnvironment.cpp
        BasicUsageEnvironment0.cpp
        DelayQueue.cpp
)

set(public_header_files
    include/BasicHashTable.hh
    include/BasicUsageEnvironment.hh
    include/BasicUsageEnvironment0.hh
    include/BasicUsageEnvironment_version.hh
    include/DelayQueue.hh
    include/HandlerSet.hh
)

add_library(BasicUsageEnvironment STATIC ${src_files} ${public_header_files})
set_target_properties(BasicUsageEnvironment PROPERTIES PUBLIC_HEADER "${public_header_files}")
install(TARGETS BasicUsageEnvironment EXPORT BasicUsageEnvironmentTargets RUNTIME DESTINATION bin ARCHIVE DESTINATION lib LIBRARY DESTINATION lib PUBLIC_HEADER DESTINATION include)
install(EXPORT BasicUsageEnvironmentTargets DESTINATION cmake)
