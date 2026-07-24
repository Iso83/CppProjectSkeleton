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
# Dependencies
# =========================================================

include(cmake/Dependencies.cmake)

dependencies_fetch_cppcmake()

# =========================================================
# CppCMake
# =========================================================

cppcmake_project_initialize()

if(CPPCMAKE_PROJECT_ALREADY_REGISTERED)
    return()
endif()

cppcmake_githooks_precommit()
cppcmake_version_generate()
cppcmake_project_enable_testing()

# =========================================================
# Modules
# =========================================================

# cppcmake_module_add(engine/core)
# cppcmake_module_add(demoApp)
