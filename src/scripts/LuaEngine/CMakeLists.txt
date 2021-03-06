# Copyright (C) 2014-2015 AscEmu Team <http://www.ascemu.org>

if(NOT BUILD_LUAENGINE)
  message("\tLuaEngine was skipped because BUILD_LUAENGINE is unchecked.")
  return()
endif(NOT BUILD_LUAENGINE)

# set up our project name
project(LuaEngine)


#SRCS - contains the source files that compose this project.
set(SRCS
   LUAEngine.cpp 
   )

set(HEADERS
   LUAEngine.h
   LUAFunctions.h
   )

include_directories(
   ${OPENSSL_INCLUDE_DIR}
   ${PCRE_INCLUDE_DIR}
   ${CMAKE_SOURCE_DIR}/dep/recastnavigation/Detour/Include
   ${CMAKE_SOURCE_DIR}/dep/vmaplib/include
   ${CMAKE_SOURCE_DIR}/dep/g3dlite/include
   ${CMAKE_SOURCE_DIR}/src/shared
   ${CMAKE_SOURCE_DIR}/src/world
   ${CMAKE_SOURCE_DIR}/dep/lualib
   ${CMAKE_CURRENT_SOURCE_DIR}
   ${ZLIB_INCLUDE_DIRS}
)
   
add_library(${PROJECT_NAME} SHARED ${SRCS} ${HEADERS})
target_link_libraries(${PROJECT_NAME} world lualib)

install(TARGETS ${PROJECT_NAME} RUNTIME DESTINATION ${ASCEMU_SCRIPTLIB_PATH} LIBRARY DESTINATION ${ASCEMU_SCRIPTLIB_PATH})
unset(sources)
unset(headers)
