cmake_minimum_required(VERSION 3.12)

project(GuruxDLMSCPush VERSION 1.0
                  DESCRIPTION "Gurux DLMS Push example"
                  LANGUAGES CXX)

set(TARGET dlms_push_example)

add_executable(${TARGET})

target_sources( ${TARGET} PRIVATE
  include/GXDLMSPushListener.h
  src/GXDLMSPushListener.cpp
  src/main.cpp
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
     pthread
  )
endif()
