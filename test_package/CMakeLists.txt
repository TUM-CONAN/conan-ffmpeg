cmake_minimum_required(VERSION 3.24)
project(test_package LANGUAGES C)

find_package(ffmpeg REQUIRED CONFIG)

add_executable(${PROJECT_NAME} test_package.c)
target_link_libraries(${PROJECT_NAME} PRIVATE ffmpeg::avutil)
if (TARGET ffmpeg::avdevice)
    target_compile_definitions(${PROJECT_NAME} PRIVATE HAVE_FFMPEG_AVDEVICE)
    target_link_libraries(${PROJECT_NAME} PRIVATE ffmpeg::avdevice)
endif ()
if (TARGET ffmpeg::avfilter)
    target_compile_definitions(${PROJECT_NAME} PRIVATE HAVE_FFMPEG_AVFILTER)
    target_link_libraries(${PROJECT_NAME} PRIVATE ffmpeg::avfilter)
endif ()
if (TARGET ffmpeg::avformat)
    target_compile_definitions(${PROJECT_NAME} PRIVATE HAVE_FFMPEG_AVFORMAT)
    target_link_libraries(${PROJECT_NAME} PRIVATE ffmpeg::avformat)
endif ()
if (TARGET ffmpeg::avcodec)
    target_compile_definitions(${PROJECT_NAME} PRIVATE HAVE_FFMPEG_AVCODEC)
    target_link_libraries(${PROJECT_NAME} PRIVATE ffmpeg::avcodec)
endif ()
if (TARGET ffmpeg::swscale)
    target_compile_definitions(${PROJECT_NAME} PRIVATE HAVE_FFMPEG_SWSCALE)
    target_link_libraries(${PROJECT_NAME} PRIVATE ffmpeg::swscale)
endif ()
if (TARGET ffmpeg::swresample)
    target_compile_definitions(${PROJECT_NAME} PRIVATE HAVE_FFMPEG_SWRESAMPLE)
    target_link_libraries(${PROJECT_NAME} PRIVATE ffmpeg::swresample)
endif ()
if (TARGET ffmpeg::postproc)
    target_compile_definitions(${PROJECT_NAME} PRIVATE HAVE_FFMPEG_POSTPROC)
    target_link_libraries(${PROJECT_NAME} PRIVATE ffmpeg::postproc)
endif ()
