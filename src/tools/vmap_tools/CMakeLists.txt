# Copyright (C) 2014-2016 AscEmu Team <http://www.ascemu.org>

add_subdirectory(vmap_extractor)
add_subdirectory(vmap_assembler)

if(WIN32)
	install(FILES ${CMAKE_CURRENT_SOURCE_DIR}/vmaps.bat DESTINATION ${ASCEMU_TOOLS_PATH})
else()
	install(FILES ${CMAKE_CURRENT_SOURCE_DIR}/vmaps.sh DESTINATION ${ASCEMU_TOOLS_PATH})
endif()