cmake_minimum_required (VERSION 3.16.3)

if (APPLE)
	set(CMAKE_OSX_ARCHITECTURES "arm64;x86_64")
endif()

enable_language(CXX)
enable_testing()

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

if (MSVC)
	set(CMAKE_CXX_FLAGS "/W4 /EHsc")
else()
	set(CMAKE_CXX_FLAGS "-Wall -Wextra -Wno-unknown-pragmas -pthread")
endif()

project(Prologue)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ../application)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_DEBUG ../application)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_RELEASE ../application)

include_directories(
	SYSTEM "deps/include/"
	"src/"
)

set(SOURCE_FILES
	"src/main.cpp"
)

add_executable(Calculator ${SOURCE_FILES})
