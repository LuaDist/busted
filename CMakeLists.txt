# Copyright (C) 2007-2013 LuaDist.
# Created by Peter Drahoš
# Redistribution and use of this file is allowed according to the terms of the MIT license.
# For details see the COPYRIGHT file distributed with LuaDist.
# Please note that the package source code is licensed under its own license.

project ( busted NONE )
cmake_minimum_required ( VERSION 2.8 )
include ( cmake/dist.cmake )
include ( lua )

set ( GIT_ARCHIVE_URL https://github.com/Olivine-Labs/busted/archive )
set ( SOURCE_FILE_NAME v${DIST_VERSION}.tar.gz )
set ( SOURCE_URL ${GIT_ARCHIVE_URL}/${SOURCE_FILE_NAME} )
set ( SOURCE_FILE ${CMAKE_CURRENT_BINARY_DIR}/${SOURCE_FILE_NAME} )
set ( SOURCE_DIR ${CMAKE_CURRENT_BINARY_DIR}/busted-${DIST_VERSION} )

if ( NOT EXISTS "${SOURCE_FILE}" )
  file( DOWNLOAD "${SOURCE_URL}" "${SOURCE_FILE}" )
endif ()

add_custom_command(
  OUTPUT ${SOURCE_DIR}/bin/busted_bootstrap
  COMMAND tar -xjvf ${SOURCE_FILE}
  DEPENDS ${SOURCE_FILE}
)

install_lua_module ( busted.init ${SOURCE_DIR}/src/init.lua )
install_lua_module ( busted.core ${SOURCE_DIR}/src/core.lua )
install_lua_module ( busted.done ${SOURCE_DIR}/src/done.lua )
install_lua_module ( busted.moon ${SOURCE_DIR}/src/moon.lua )

install_lua_module ( busted.languages.ar ${SOURCE_DIR}/src/languages/ar.lua )
install_lua_module ( busted.languages.de ${SOURCE_DIR}/src/languages/de.lua )
install_lua_module ( busted.languages.en ${SOURCE_DIR}/src/languages/en.lua )
install_lua_module ( busted.languages.fr ${SOURCE_DIR}/src/languages/fr.lua )
install_lua_module ( busted.languages.ja ${SOURCE_DIR}/src/languages/ja.lua )
install_lua_module ( busted.languages.nl ${SOURCE_DIR}/src/languages/nl.lua )
install_lua_module ( busted.languages.ru ${SOURCE_DIR}/src/languages/ru.lua )
install_lua_module ( busted.languages.ua ${SOURCE_DIR}/src/languages/ua.lua )
install_lua_module ( busted.languages.zh ${SOURCE_DIR}/src/languages/zh.lua )

install_lua_module ( busted.loop.copas ${SOURCE_DIR}/src/loop/copas.lua )
install_lua_module ( busted.loop.default ${SOURCE_DIR}/src/loop/default.lua )
install_lua_module ( busted.loop.ev ${SOURCE_DIR}/src/loop/ev.lua )

install_lua_module ( busted.output.TAP ${SOURCE_DIR}/src/output/TAP.lua )
install_lua_module ( busted.output.json ${SOURCE_DIR}/src/output/json.lua )
install_lua_module ( busted.output.junit ${SOURCE_DIR}/src/output/junit.lua )
install_lua_module ( busted.output.plain_terminal ${SOURCE_DIR}/src/output/plain_terminal.lua )
install_lua_module ( busted.output.stub ${SOURCE_DIR}/src/output/stub.lua )
install_lua_module ( busted.output.utf_terminal ${SOURCE_DIR}/src/output/utf_terminal.lua )

install_lua_executable ( busted ${SOURCE_DIR}/bin/busted_bootstrap )
install_data ( ${SOURCE_DIR}/README.md ${SOURCE_DIR}/LICENSE ${SOURCE_DIR}/CONTRIBUTING.md )
