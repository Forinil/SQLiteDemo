cmake_minimum_required(VERSION 3.16)
project(sqlite33)

add_library(sqlite3 STATIC sqlite3.c)

install(TARGETS sqlite3 DESTINATION lib)
install(FILES sqlite3.h DESTINATION include)