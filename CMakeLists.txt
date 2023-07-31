cmake_minimum_required(VERSION 3.22)

# Enable Hot Reload for MSVC compilers if supported.
if (POLICY CMP0141)
  cmake_policy(SET CMP0141 NEW)
  set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")
endif()

project("Template" LANGUAGES CXX)
set(CMAKE_CXX_STANDARD 20)

# Find libraries
find_package(raylib REQUIRED)

# Compile to executable
set(EXECUTABLE "Template")

# Source files
file(GLOB SOURCES "Source/*.cpp")
add_executable (${EXECUTABLE} ${SOURCES})

# Header files
include_directories("Include/")

# Link libraries
target_link_libraries(${EXECUTABLE}
	PRIVATE
		raylib)
