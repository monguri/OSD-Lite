#
#   Copyright 2013 Pixar
#
#   Licensed under the Apache License, Version 2.0 (the "Apache License")
#   with the following modification; you may not use this file except in
#   compliance with the Apache License and the following modification to it:
#   Section 6. Trademarks. is deleted and replaced with:
#
#   6. Trademarks. This License does not grant permission to use the trade
#      names, trademarks, service marks, or product names of the Licensor
#      and its affiliates, except as required to comply with Section 4(c) of
#      the License and to reproduce the content of the NOTICE file.
#
#   You may obtain a copy of the Apache License at
#
#       http://www.apache.org/licenses/LICENSE-2.0
#
#   Unless required by applicable law or agreed to in writing, software
#   distributed under the Apache License with the above modification is
#   distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
#   KIND, either express or implied. See the Apache License for the specific
#   language governing permissions and limitations under the Apache License.
#

# source & headers
set(SOURCE_FILES
     fvarLevel.cpp
     fvarRefinement.cpp
     level.cpp
     quadRefinement.cpp
     refinement.cpp
     sparseSelector.cpp
     triRefinement.cpp
)

set(PRIVATE_HEADER_FILES
     quadRefinement.h
     triRefinement.h
)

set(PUBLIC_HEADER_FILES
     array.h
     componentInterfaces.h
     fvarLevel.h
     fvarRefinement.h
     level.h
     refinement.h
     sparseSelector.h
     stackBuffer.h
     types.h
)

# Compile objs first for both the CPU and GPU libs -----
add_library(osd_lite_vtr_obj OBJECT
        ${SOURCE_FILES}
        ${PRIVATE_HEADER_FILES}
        ${PUBLIC_HEADER_FILES}
)

target_include_directories(osd_lite_vtr_obj PRIVATE "${CMAKE_CURRENT_BINARY_DIR}")

set_target_properties(osd_lite_vtr_obj PROPERTIES POSITION_INDEPENDENT_CODE TRUE FOLDER "${OSD_LITE_FOLDER_NAME}")

install(
    FILES
        ${PUBLIC_HEADER_FILES}
    DESTINATION
        "include/opensubdiv/vtr"
    PERMISSIONS
        OWNER_READ
        GROUP_READ
        WORLD_READ )

