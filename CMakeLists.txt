cmake_minimum_required(VERSION 3.15)

# --------------------------------------------------
# Project
# --------------------------------------------------
project(SpeedTreeRT
    VERSION 1.0
    LANGUAGES CXX
)

# --------------------------------------------------
# C++ Standard (GLOBAL)
# --------------------------------------------------
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# --------------------------------------------------
# Kaynaklar
# --------------------------------------------------
set(SOURCE_FILES
    src/LibRandom_Source/ExtendedReal.cpp
    src/LibRandom_Source/IdvRandom.cpp
    src/LibRandom_Source/RobertDavies_Random.cpp
    src/LibSpline_Source/IdvSpline.cpp
    src/LibVector_Source/Region.cpp
    src/LibVector_Source/RotTransform.cpp
    src/LibVector_Source/Transform.cpp
    src/LibVector_Source/Vec.cpp
    src/LibVector_Source/Vec3.cpp

    src/BillboardLeaf.cpp
    src/Branch.cpp
    src/BranchGeometry.cpp
    src/BranchInfo.cpp
    src/Camera.cpp
    src/FileAccess.cpp
    src/FrondEngine.cpp
    src/IndexedGeometry.cpp
    src/LeafGeometry.cpp
    src/LeafInfo.cpp
    src/LeafLod.cpp
    src/LightingEngine.cpp
    src/ProjectedShadow.cpp
    src/SimpleBillboard.cpp
    src/SpeedTreeRT.cpp
    src/TreeEngine.cpp
    src/TreeInfo.cpp
    src/WindEngine.cpp
    src/WindInfo.cpp
)

# --------------------------------------------------
# Static library
# --------------------------------------------------
add_library(speedtree_static STATIC ${SOURCE_FILES})

target_include_directories(speedtree_static
    PUBLIC
        ${CMAKE_CURRENT_SOURCE_DIR}/include
)

target_compile_definitions(speedtree_static
    PRIVATE SPEEDTREE_RETAIL
)

# --------------------------------------------------
# Shared library
# --------------------------------------------------
add_library(speedtree_shared SHARED ${SOURCE_FILES})

set_target_properties(speedtree_shared PROPERTIES
    OUTPUT_NAME SpeedTreeRT
)

target_include_directories(speedtree_shared
    PUBLIC
        ${CMAKE_CURRENT_SOURCE_DIR}/include
)

target_compile_definitions(speedtree_shared
    PRIVATE
        SPEEDTREE_RETAIL
        SPEEDTREERT_DYNAMIC_LIB
        IDV_SPEEDTREERT_EXPORTS
)

# --------------------------------------------------
# Compiler-specific ayarlar
# --------------------------------------------------
if (MSVC)
    target_compile_options(speedtree_static PRIVATE /EHsc)
    target_compile_options(speedtree_shared PRIVATE /EHsc)
else()
    target_compile_options(speedtree_static PRIVATE -fexceptions)
    target_compile_options(speedtree_shared PRIVATE -fexceptions)
endif()
