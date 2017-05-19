cmake_minimum_required(VERSION 3.5)

project(ros1_lifecycle_msgs)

if(NOT WIN32)
  set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++14 -Wall -Wextra")
endif()

set(msg_deps
  std_msgs
)

find_package(catkin REQUIRED COMPONENTS
  ${msg_deps}
  message_generation
)

set(msg_files
  "State.msg"
  "Transition.msg"
  "TransitionDescription.msg"
  "TransitionEvent.msg"
)
set(srv_files
  "ChangeState.srv"
  "GetAvailableStates.srv"
  "GetAvailableTransitions.srv"
  "GetState.srv"
)

add_message_files(FILES ${msg_files})
add_service_files(FILES ${srv_files})

generate_messages(DEPENDENCIES ${msg_deps})

catkin_package(CATKIN_DEPENDS
  ${msg_deps}
  message_runtime
 )
