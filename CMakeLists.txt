# Copyright (C) 2007-2013 LuaDist.
# Created by Peter Drahoš
# Redistribution and use of this file is allowed according to the terms of the MIT license.
# For details see the COPYRIGHT file distributed with LuaDist.
# Please note that the package source code is licensed under its own license.

project ( busted NONE )
cmake_minimum_required ( VERSION 2.8 )
include ( cmake/dist.cmake )
include ( lua )

install_lua_module ( busted.core src/core.lua )
install_lua_module ( busted.output.utf_terminal src/output/utf_terminal.lua )
install_lua_module ( busted.output.plain_terminal src/output/plain_terminal.lua )
install_lua_module ( busted.output.TAP src/output/TAP.lua )
install_lua_module ( busted.output.json src/output/json.lua )
install_lua_module ( busted.output.junit src/output/junit.lua )
install_lua_module ( busted.init src/init.lua )
install_lua_module ( busted.languages.en src/languages/en.lua )
install_lua_module ( busted.languages.ar src/languages/ar.lua )
install_lua_module ( busted.languages.fr src/languages/fr.lua )
install_lua_module ( busted.languages.nl src/languages/nl.lua )
install_lua_module ( busted.languages.ru src/languages/ru.lua )
install_lua_module ( busted.languages.ua src/languages/ua.lua )
install_lua_module ( busted.languages.zh src/languages/zh.lua )

install_lua_executable ( busted bin/busted_bootstrap )
install_data ( README.md LICENSE CONTRIBUTING.md )
