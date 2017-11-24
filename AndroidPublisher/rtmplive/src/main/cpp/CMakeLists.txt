
cmake_minimum_required(VERSION 3.4.1)
set(rtmp_dir ${CMAKE_SOURCE_DIR}/../../../../rtmp)
set(rtmp_lib_dir ${rtmp_dir}/lib)
#添加头文件目录
include_directories(${rtmp_dir}/include/librtmp)

add_library( publish
    SHARED
    publish_jni.cpp
    Rtmp.cpp

    librtmp/amf.c
    librtmp/amf.h
    librtmp/bytes.h
    librtmp/dh.h
    librtmp/dhgroups.h
    librtmp/handshake.h
    librtmp/hashswf.c
    librtmp/http.h
    librtmp/log.c
    librtmp/log.h
    librtmp/parseurl.c
    librtmp/rtmp.c
    librtmp/rtmp.h
    librtmp/rtmp_sys.h
    )

include_directories(librtmp)

add_definitions(-DNO_CRYPTO)

find_library(
              log-lib
              log )

#librtmp

#add_library(rtmp SHARED IMPORTED)
#set_target_properties(rtmp PROPERTIES IMPORTED_LOCATION
                      #${rtmp_lib_dir}/${ANDROID_ABI}/librtmp.so)

#target_link_libraries( publish
                       #${log-lib}
                      #rtmp
                        #)
target_link_libraries(publish ${log-lib})
