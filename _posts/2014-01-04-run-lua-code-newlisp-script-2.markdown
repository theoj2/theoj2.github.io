---
author: tjones
comments: false
date: 2014-01-04 17:19:33+00:00
layout: post
slug: run-lua-code-newlisp-script-2
title: Run Lua Code in a NewLISP Script
wordpress_id: 1081
categories:
- old
tags:
- LUA
- Old
---

Below is the code for a NewLISP context that uses the Lua API to run Lua code. Its not yet a full binding, however.It works by using NewLISP's FFI interface to load the Lua .so file. So far it only works with Linux and assumes that the Lua library is located in /usr/lib/liblua.so. There are three functions InitLUA , which creates a Lua state and then loads the Lua standard libraries. RunLuaCodeFromString which executes a string of Lua code. RunLuaCodeFromFile which executes the code contained in a file.   

`.   

(context 'LUA)
(constant 'PathToLuaLib "/usr/lib/liblua.so")
(constant 'LUA_MULTRET -1)
(import PathToLuaLib "luaL_newstate")
(import PathToLuaLib "luaL_loadstring")
;(import PathToLuaLib "luaL_loadfilex")
;(import PathToLuaLib "lua_register")
(import PathToLuaLib "lua_pcallk")
(import PathToLuaLib "luaL_openlibs")





(define (InitLUA)
    (set '_lua_State_ (luaL_newstate))  ;; *lua_State* is a pointer to a lua_State struct 
    (luaL_openlibs _lua_State_)
)





(define (RunLuaCodeFromString LuaCode)
    (luaL_loadstring *lua_State* LuaCode)
    (lua_pcallk *lua_State* 0 LUA_MULTRET 0)
)





(define (RunLuaCodeFromFile filename)
    (RunLuaCodeFromString (read-file filename))  ;; There is a function to do this in the Lua api but this seems cleaner.
)





(InitLUA)
;(RunLuaCodeFromString "print('hello world')")
;(RunLuaCodeFromFile "hello.lua")





(context MAIN)
`
