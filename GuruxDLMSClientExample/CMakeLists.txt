cmake_minimum_required(VERSION 3.12)

project(GuruxDLMSClient VERSION 1.0
                  DESCRIPTION "Gurux DLMS Client example"
                  LANGUAGES CXX C)

set(TARGET dlms_client_example)

add_executable(${TARGET})

target_sources( ${TARGET} PRIVATE
  include/communication.h
  include/getopt.h
  src/getopt.c
  src/communication.cpp
  src/GuruxDLMSClientExample.cpp
)

target_link_libraries(${TARGET} PRIVATE
  gurux_dlms_cpp
)

if(WIN32)
  target_link_libraries(${TARGET} PRIVATE
     ws2_32
  )    
elseif(UNIX)
  target_link_libraries(${TARGET} PRIVATE
     m
  )
endif()
