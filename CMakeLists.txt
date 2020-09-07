project(mysql C)

cmake_minimum_required(VERSION 3.16.0)

set(CMAKE_WINDOWS_EXPORT_ALL_SYMBOLS 1)

add_library(mysql SHARED src/luasql.h src/luasql.c src/ls_mysql.c)

target_include_directories(mysql PUBLIC deps/module-sdk/include)
target_include_directories(mysql PUBLIC ${MYSQL_DIR}/include)

if(WIN32)
    target_link_libraries(mysql PRIVATE "${CMAKE_SOURCE_DIR}/deps/module-sdk/lib/lua.lib")
    target_link_libraries(mysql PUBLIC "${MYSQL_DIR}/lib/libmysql.lib")
    target_link_libraries(mysql PUBLIC "${MYSQL_DIR}/lib/mysqlclient.lib")
elseif(UNIX AND NOT APPLE)
    target_link_libraries(mysql PRIVATE "${CMAKE_SOURCE_DIR}/deps/module-sdk/lib/liblua.a")
    target_link_libraries(mysql PUBLIC "${MYSQL_DIR}/lib/libmysqlclient.a")
    target_link_libraries(mysql PUBLIC ssl crypto z)
endif()