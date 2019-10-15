cmake_minimum_required(VERSION 2.8)

project(demo3)

# 查找当前目录下的所有源文件
# 并将名称保存到 DIR_SRCS 变量
#aux_source_directory(. DIR_SRCS)

add_subdirectory(math)

add_executable(demo main.cc)
target_link_libraries(demo MathFunctions)