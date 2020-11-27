  
CMAKE_MINIMUM_REQUIRED (VERSION 3.13.0)
PROJECT (gha_boost)
find_package(Boost REQUIRED)
list (APPEND exec_programs
    test.cpp
)

foreach (source_file ${exec_programs})
    get_filename_component (source_file_we ${source_file} NAME_WE)
    add_executable (
        ${source_file_we}
        ${source_file}
    )
endforeach ()
