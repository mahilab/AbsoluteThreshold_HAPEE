cmake_minimum_required(VERSION 3.13)

#===============================================================================
# MY PROJECT
#===============================================================================

# create project
project(AbsoluteThreshold_AIMS_Str-Squ VERSION 0.1.0 LANGUAGES CXX)

# find MEL::MEL and all available MEL::xxx modules
find_package(MEL REQUIRED)

# include directories
include_directories(
    "include"              # your include directory
    "C:/Program Files (x86)/National Instruments/Shared/ExternalCompilerSupport/C/include" # NIDAQ's include directory
    "C:/Program Files (x86)/maxon motor ag/EPOS Positioning Controller/EPOS4/04 Programming/Windows DLL/Microsoft Visual C++/Definition Files" # EPOS4's directory
)

# indicate where all used .lib are
link_directories(
	"C:/Program Files (x86)/National Instruments/Shared/ExternalCompilerSupport/C/lib64/msvc" # NIDAQ's lib file
    "C:/Program Files (x86)/maxon motor ag/EPOS Positioning Controller/EPOS4/04 Programming/Windows DLL/Microsoft Visual C++/Definition Files" # EPOS4's directory
)

# remove or uncomment if linking MEL statically
# add_definitions(-DMEL_STATIC)

# create application
add_executable(absolute_threshold_tests
    include/maxon_motor.hpp
    include/absolute_triallist.hpp
    include/absolute_staircase.hpp
    include/daq_ni.hpp
    src/maxon_motor.cpp
    src/absolute_triallist.cpp
    src/absolute_staircase.cpp
    src/daq_ni.cpp
    src/test_main.cpp
)

# link MEL
target_link_libraries(absolute_threshold_tests
    MEL::MEL
    MEL::quanser
    NIDAQmx.lib
    EposCmd64.lib
)
