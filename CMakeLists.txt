# Copyright 2012 Jared Boone
# Copyright 2013/2014 Benjamin Vernoux
#
# This file is part of AirSpy (based on HackRF project).
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2, or (at your option)
# any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; see the file COPYING.  If not, write to
# the Free Software Foundation, Inc., 51 Franklin Street,
# Boston, MA 02110-1301, USA.
#

# Based heavily upon the libftdi cmake setup.

set(INSTALL_DEFAULT_BINDIR "bin" CACHE STRING "Appended to CMAKE_INSTALL_PREFIX")

add_executable(airspy_rx airspy_rx.c)
install(TARGETS airspy_rx RUNTIME DESTINATION ${INSTALL_DEFAULT_BINDIR})

include_directories(/usr/local/include/libairspy)

if(NOT libairspy_SOURCE_DIR)
    include_directories(${LIBAIRSPY_INCLUDE_DIR})
    LIST(APPEND TOOLS_LINK_LIBS ${LIBAIRSPY_LIBRARIES})
else()
    LIST(APPEND TOOLS_LINK_LIBS airspy)
endif()

target_link_libraries(airspy_rx /usr/local/lib/libairspy.a /usr/local/lib/libusb-1.0.a)
