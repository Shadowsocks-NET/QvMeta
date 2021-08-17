cmake_minimum_required(VERSION 3.20)

project(QvPersonal-MetaRepo)

set(QV2RAY_STATIC_PLUGINS ON)
set(BUILD_SHARED_LIBS OFF)
set(CMAKE_INCLUDE_CURRENT_DIR ON)

# Properly set CMake prefix path
# set(CMAKE_PREFIX_PATH "/tmp/qt-build/static-installed/lib/cmake")

find_package(Qt6 COMPONENTS Core Gui Widgets Network)
add_subdirectory(QvPersonal)

option(ALL_PLUGINS "Build with all plugins" ON)

macro(plugin_collection name)
    option("HAS_PLUGIN_${name}" ${ALL_PLUGINS})
    if(${HAS_PLUGIN_${name}} OR ALL_PLUGINS)
        add_subdirectory(Plugins/QvPlugin-${name})
        message("|| State || QvPlugin-${name}: ON")
    else()
        message("|| State || QvPlugin-${name}: OFF")
    endif()
endmacro()

#plugin_collection(Command)
#plugin_collection(Trojan-Go)
plugin_collection(NaiveProxy)
plugin_collection(LatencyTest)
