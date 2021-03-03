cmake_minimum_required(VERSION 3.12)

set (app_inc ${PROJECT_SOURCE_DIR}/inc)
set (app_cfg ${PROJECT_SOURCE_DIR}/cfg)

include_directories(${app_inc})


# 是否使用自己的 Math库
option (USE_MYMATH "Use provided math implementation" ON)
# 用于测试替换用的变量
set(TEST_ON 1)
set(TEST_OF 0)
set(CONFIG_VAR "DEBUG")

# 加入一个配置头文件，用于处理 CMake 对源码的设置
configure_file (
  "${app_cfg}/config.h.in"
  "${app_inc}/config.h"
)

if (USE_MYMATH)
    set(APP_SRC t_main.c ../alg/debug.c)
    message(STATUS "src This is BINARY dir " ${PROJECT_BINARY_DIR})
    message(STATUS "src This is SOURCE dir " ${PROJECT_SOURCE_DIR})
else (USE_MYMATH)
    aux_source_directory(. APP_SRC)
endif (USE_MYMATH)

set(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/bin)

set (EXTRA_LIBS alg)

add_executable(test ${APP_SRC})

TARGET_LINK_LIBRARIES(test ${EXTRA_LIBS})