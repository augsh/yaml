project(yaml)

add_library(${PROJECT_NAME} INTERFACE IMPORTED GLOBAL)
target_include_directories(${PROJECT_NAME}
                           INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}/include)
file(GLOB_RECURSE SO_FILES "lib/*.so")
target_link_libraries(${PROJECT_NAME} INTERFACE ${SO_FILES})

if(NOT ${OUT} STREQUAL "")
  message("Set output directory to ${OUT}")
  file(GLOB_RECURSE LIBS "lib/lib*")
  file(COPY ${LIBS} DESTINATION ${OUT_LIB})
endif()
