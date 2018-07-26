#########################################################################
# CMakeLists.txt file for building                      #
#                                                                       #
# Copyright (c) 2013 Leopold Palomo-Avellaneda <leo@alaxarxa.net>       #
#                                                                       #
# This file is free software: you can redistribute it and/or modify     #
# it under the terms of the GNU General Public License as published by  #
# the Free Software Foundation, either version 3 of the License, or     #
# (at your option) any later version.                                   #
#                                                                       #
# This program is distributed in the hope that it will be useful,       #
# but WITHOUT ANY WARRANTY; without even the implied warranty of        #
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the         #
# GNU General Public License for more details.                          #
#                                                                       #
# You should have received a copy of the GNU General Public License     #
# along with this program.  If not, see <http://www.gnu.org/licenses/>. #
#########################################################################

cmake_minimum_required (VERSION 2.8.12)

project(xenocmake)

# Needed Modules
include(GNUInstallDirs)
include(CMakePackageConfigHelpers)
include(FindPkgConfig)
include(${PROJECT_SOURCE_DIR}/cmake-modules/CMakeFunctions.cmake)

# Set policy for LINK_INTERFACE
cmake_policy(SET CMP0022 NEW)

set(CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/cmake-modules)

#common commands for building c++ executables and libraries
# try Xenomai
# find Xenomai
find_package(Xenomai)

if(Xenomai_FOUND)
    message("Xenomai Native includes : ${Xenomai_NATIVE_INCLUDE_DIRS}" )
    message("Xenomai Native definitions: ${Xenomai_NATIVE_DEFINITIONS}")
    message("Xenomai Native LIBRARY_DIRS : ${Xenomai_NATIVE_LIBRARY_DIRS}")
    message("Xenomai Native LIBRARIES : ${Xenomai_NATIVE_LIBRARIES}")
    message("Xenomai Native LDFLAGS : ${Xenomai_NATIVE_LDFLAGS}")
    message("Xenomai Native DL_FLAGS : ${Xenomai_NATIVE_DL_FLAGS}")
endif(Xenomai_FOUND)

add_subdirectory(src)
