  
CMAKE_MINIMUM_REQUIRED (VERSION 3.13.0)
PROJECT (gha_boost)
find_package(Boost REQUIRED COMPONENTS log)
list (APPEND exec_programs
    hello.cpp
)

foreach (source_file ${exec_programs})
    get_filename_component (source_file_we ${source_file} NAME_WE)
    add_executable (
        ${source_file_we}
        ${source_file}
    )
    TARGET_COMPILE_DEFINITIONS (${source_file_we} PUBLIC BOOST_LOG_DYN_LINK)
    TARGET_LINK_LIBRARIES (
        ${source_file_we} Boost::log
    )    
endforeach ()
