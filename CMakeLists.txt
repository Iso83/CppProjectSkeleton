cmake_minimum_required(VERSION 3.24)

project(MyProject
    VERSION 0.1.0
    LANGUAGES CXX
)

# =========================================================
# Project configuration
# =========================================================

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

set_property(GLOBAL PROPERTY USE_FOLDERS ON)

# =========================================================
# CppCMake
# =========================================================

include(cmake/Dependencies.cmake)

dependencies_fetch_cppcmake()

cppcmake_project_initialize()

if(CPPCMAKE_PROJECT_ALREADY_REGISTERED)
    return()
endif()

cppcmake_githook_precommit()
cppcmake_version_generate()
cppcmake_test_setup()

# =========================================================
# Dependencies
# =========================================================

#
# Add project dependencies here.
#
# Examples:
#
#   - FetchContent + cppcmake_dependency_make_available(...)
#   - cppcmake_dependency_add_subdirectory(...)
#
# Optionally group dependency targets in the IDE using:
#
#   cppcmake_dependency_set_folder(...)
#

# =========================================================
# Modules
# =========================================================

#
# Register project modules here.
#
# Examples:
#
#   cppcmake_module_add(engine/core)
#   cppcmake_module_add(engine/math)
#
#   cppcmake_module_add(apps/demo)
#   cppcmake_module_add(apps/editor)
#
