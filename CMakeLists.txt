cmake_minimum_required (VERSION 2.8.11)
PROJECT(WSAOSC)
SET(VERSION_MAJOR       "0")
SET(VERSION_MINOR       "1")
SET(VERSION_RELEASE     "0")
SET(VERSION             "${VERSION_MAJOR}.${VERSION_MINOR}.${VERSION_RELEASE}")


INCLUDE (CheckIncludeFiles)

check_include_files(windows.h WSAOSC_HAVE_WINDOWS_H)
check_include_files(shellapi.h WSAOSC_HAVE_SHELLAPI_H)

IF((NOT DEFINED ${WSAOSC_HAVE_WINDOWS_H}) OR (NOT DEFINED ${WSAOSC_HAVE_SHELLAPI_H}))
  message(FATAL_ERROR "This software is only effective on Microsoft(R) Windows(R).")
ENDIF()

add_executable(wsaosc main.c)
target_include_directories(wsaosc PUBLIC ${CMAKE_SOURCE_DIR})
