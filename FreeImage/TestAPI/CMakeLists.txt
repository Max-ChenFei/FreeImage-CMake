cmake_minimum_required(VERSION 3.16.6)
project(FreeImageTest VERSION 3.18.0)

file(GLOB SOURCE_FILES ${CMAKE_CURRENT_SOURCE_DIR}/*.cpp)
add_executable(${PROJECT_NAME} ${SOURCE_FILES})

set(${PROJECT_NAME}_INCLUDE_DIR ${CMAKE_CURRENT_SOURCE_DIR})
target_include_directories(${PROJECT_NAME} PRIVATE ${${PROJECT_NAME}_INCLUDE_DIR})
set(FreeImageTargetName FreeImage)
target_link_libraries(${PROJECT_NAME} PRIVATE ${FreeImageTargetName})
add_dependencies(${PROJECT_NAME} ${FreeImageTargetName})

# copy the test data
set(${PROJECT_NAME}_TESTDATA_DIR ${CMAKE_CURRENT_SOURCE_DIR})
add_custom_command(TARGET ${PROJECT_NAME} POST_BUILD
				   COMMAND ${CMAKE_COMMAND} -E copy
				   		   "${${PROJECT_NAME}_TESTDATA_DIR}/exif.jpg"
						   "${${PROJECT_NAME}_TESTDATA_DIR}/exif.jxr"
						   "${${PROJECT_NAME}_TESTDATA_DIR}/sample.png"
   						   "${CMAKE_BINARY_DIR}/TestAPI/$<CONFIG>/")

# Copying dependent DLLs to executable directory after building the target on Windows
if(MSVC)
	add_custom_command(TARGET ${PROJECT_NAME} POST_BUILD
					   COMMAND ${CMAKE_COMMAND} -E copy
							  "${${FreeImageTargetName}_BINARY_DIR}/$<CONFIG>/${FreeImageTargetName}$<$<CONFIG:Debug>:d>.dll"
							  "${CMAKE_CURRENT_BINARY_DIR}/$<CONFIG>/")
endif(MSVC)
