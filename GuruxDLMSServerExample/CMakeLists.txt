cmake_minimum_required(VERSION 3.12)

project(GuruxDLMSServer VERSION 1.0
                  DESCRIPTION "Gurux DLMS Server example"
                  LANGUAGES CXX C)

set(TARGET dlms_server_example)

add_executable(${TARGET})

target_sources( ${TARGET} PRIVATE
  include/getopt.h
  include/GXDLMSServerSN.h
  include/GXDLMSServerLN_47.h
  include/GXDLMSBase.h
  include/GXDLMSServerSN_47.h
  include/GXDLMSServerLN.h
  src/getopt.c
  src/GXDLMSBase.cpp
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
