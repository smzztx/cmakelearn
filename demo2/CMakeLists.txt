cmake_minimum_required(VERSION 2.8)

project(demo2)

# 查找当前目录下的所有源文件
# 并将名称保存到 DIR_SRCS 变量
aux_source_directory(. DIR_SRCS)

# add_executable(demo main.cc MathFunctions.cc)
add_executable(demo main.cc ${DIR_SRCS})