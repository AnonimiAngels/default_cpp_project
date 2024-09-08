cmake_minimum_required(VERSION 3.29)

include(./utilities.cmake)

project(${PROJECT_NAME})

collect_subdirectories(${PROJECT_DIR}/src SRC_DIRS)
collect_subdirectories(${PROJECT_DIR}/inc INC_DIRS)

file(GLOB_RECURSE PROJECT_SOURCES ${SRC_DIRS}/*.cpp ${SRC_DIRS}/*.c)
file(GLOB_RECURSE PROJECT_HEADERS ${INC_DIRS}/*.hpp ${INC_DIRS}/*.h)

message(STATUS "Project src_dirs: ${SRC_DIRS}")
message(STATUS "Project inc_dirs: ${INC_DIRS}")

find_package(spdlog REQUIRED)

set(LIBRARIES spdlog::spdlog)

# Set the output directory for the built executable
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

# Add include directories
include_directories(${INC_DIRS})

# Create the executable
add_executable(${PROJECT_NAME} ${PROJECT_SOURCES})

# Link any libraries
target_link_libraries(${PROJECT_NAME} ${LIBRARIES})

# Post build commands (copying files, etc.)
add_custom_command(TARGET ${PROJECT_NAME} POST_BUILD
	# Copy executable to the ${PROJECT_DIR}/bin/ directory
	COMMAND ${CMAKE_COMMAND} -E echo "Copying $<TARGET_FILE:${PROJECT_NAME}> to ${PROJECT_DIR}/bin/"
	COMMAND ${CMAKE_COMMAND} -E copy $<TARGET_FILE:${PROJECT_NAME}> ${PROJECT_DIR}/bin/
)