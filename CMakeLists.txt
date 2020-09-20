cmake_minimum_required(VERSION 2.8)
project(demo)
add_definitions(-DCMAKE_EXPORT_COMPILE_COMMANDS=ON)

# 编译器和C++标准
# set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
# set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++14")
# set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++17")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++20")
# set(CMAKE_CXX_FLAGS "-nostdinc++ -std=c++17 -nodefaultlibs -lc++ -lc++abi -lm -lc -lgcc_s -lgcc") # g++使用libc++
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -stdlib=libc++ -Wl,-rpath,'/home/zhm/bin/llvm/lib'") # clang++, -Wl选项用来比避免lldb-mi找不到链接库
# set(LIBRARIES_TO_LINK "c++abi")

# 头文件搜索路径
include_directories(include)
# 第三方库
include_directories(./third_party/include)
# add_subdirectory(./third_party/)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -L${PROJECT_SOURCE_DIR}/third_party/lib")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wl,-rpath,'$ORIGIN/third_party/lib/':'$ORIGIN/../third_party/lib/'") # 第三方库查找路径

# 业务相关
# set(Boost_USE_STATIC_LIBS ON)
# find_package(Boost REQUIRED COMPONENTS system)
add_executable(main main.cpp)
# target_link_libraries(main boost_system)
