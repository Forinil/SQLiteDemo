cmake_minimum_required(VERSION 3.16)
project(SQLiteDemo)

set(CMAKE_CXX_STANDARD 14)

add_executable(SQLiteDemo main.cpp)
add_subdirectory(sqlite3)
target_include_directories(SQLiteDemo PUBLIC sqlite3)
target_link_libraries(SQLiteDemo PRIVATE sqlite3)


if (UNIX)
    set(THREADS_PREFER_PTHREAD_FLAG ON)
    find_package(Threads REQUIRED)
    target_link_libraries(SQLiteDemo PRIVATE Threads::Threads)
    target_link_libraries(SQLiteDemo PRIVATE ${CMAKE_DL_LIBS})
endif()

install(TARGETS SQLiteDemo DESTINATION bin)