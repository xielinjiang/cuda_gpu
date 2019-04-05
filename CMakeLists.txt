project(PRO)    # 指定项目名称
cmake_minimum_required(VERSION 2.8)
add_subdirectory(cuda ./cuda/bin) # 将子目录添加到构建中

add_subdirectory(src ./src/bin)

set(EXTRA_LIBS ${EXTRA_LIBS} cube print) # 用来显示定义变量
set(CMAKE_C_COMPILER g++)  # 指定C编译器为 g++

# list(LENGTH <list><output variable>)  返回列表长度
# list(GET <list> <elementindex> [<element index> ...] <output variable>) 返回列表中指定下标元素
# list(APPEND <list><element> [<element> ...])  添加新元素到列表中
# list(FIND <list> <value><output variable>)    
# list(INSERT <list><element_index> <element> [<element> ...])  将新元素插入到列表中指定的位置
# list(REMOVE_ITEM <list> <value>[<value> ...])  从列表中删除某个元素
# list(REMOVE_AT <list><index> [<index> ...])   从列表中删除指定下标的元素
# list(REMOVE_DUPLICATES <list>)    从列表中删除重复的元素
# list(REVERSE <list>)  将列表的内容实地反转，改变的是列表本身，而不是其副本
# list(SORT <list>) 将列表按字母顺序实地排序，改变的是列表本身，而不是其副本
list(APPEND CMAKE_C_FLAGS "-lstdc++") # 编译C文件时的选项
 
add_executable(pro main.c)
target_link_libraries(pro ${EXTRA_LIBS})