
cmake_minimum_required(VERSION 2.8.12)

project("generated_code")

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_EXTENSIONS OFF)

# Find requirements
find_package(fastcdr REQUIRED)
find_package(fastrtps REQUIRED)


message(STATUS "Configuring VecMsg...")
add_library(VecMsg_lib VecMsg.cxx)
target_link_libraries(VecMsg_lib fastcdr fastrtps)

add_executable(VecMsg VecMsgPubSubTypes.cxx VecMsgPublisher.cxx VecMsgSubscriber.cxx VecMsgPubSubMain.cxx)
target_link_libraries(VecMsg fastcdr fastrtps
        VecMsg_lib )



