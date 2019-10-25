INCLUDE_DIRECTORIES(/usr/local/include/hello)

ADD_EXECUTABLE(main main.c)

TARGET_LINK_LIBRARIES(main /usr/local/lib/libhello.a)