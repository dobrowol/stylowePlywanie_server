project(StylowePlywanieServer)
cmake_minimum_required(VERSION 2.8.2)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++1z -g")
aux_source_directory(. SRC_LIST)
find_package (Threads)
find_package(Boost)
find_package(Boost COMPONENTS system)
message (WARNING ${Boost_SYSTEM_LIBRARY})
include_directories(${Boost_INCLUDE_DIR})
add_executable(${PROJECT_NAME} server.cpp)
target_link_libraries (${PROJECT_NAME} ${CMAKE_THREAD_LIBS_INIT} ${Boost_SYSTEM_LIBRARY} ${Boost_LIBRARIES})
add_executable(Client client.cpp)
target_link_libraries (Client ${CMAKE_THREAD_LIBS_INIT} ${Boost_SYSTEM_LIBRARY} ${Boost_LIBRARIES})
add_executable(Timer async_timer.cpp)
target_link_libraries (Timer ${CMAKE_THREAD_LIBS_INIT} ${Boost_SYSTEM_LIBRARY} ${Boost_LIBRARIES})
