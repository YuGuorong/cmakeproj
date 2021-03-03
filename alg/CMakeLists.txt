cmake_minimum_required(VERSION 3.12)
# 查找当前目录下的所有源文件

# 并将名称保存到 DIR_LIB_SRCS 变量
include_directories(${PROJECT_SOURCE_DIR}/inc)

aux_source_directory(. DIR_LIB_SRCS)

set(LIBRARY_OUTPUT_PATH ${PROJECT_BINARY_DIR}/lib)

# 生成链接库
add_library (alg ${DIR_LIB_SRCS})
