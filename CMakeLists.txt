cmake_minimum_required(VERSION 3.5)

project(qss)

if(NOT TARGET Qt6::Core)
find_package(Qt6 REQUIRED COMPONENTS Core)
endif()

file(GLOB SRCS "src/*.cpp" "include/*.h")
add_library(${PROJECT_NAME} STATIC ${SRCS})
set_target_properties(${PROJECT_NAME} PROPERTIES AUTOMOC OFF AUTOUIC OFF AUTORCC OFF)
target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include)
target_link_libraries(${PROJECT_NAME} Qt::Core)

add_executable(test_${PROJECT_NAME} test/test.cpp)
target_link_libraries(test_${PROJECT_NAME} Qt::Core ${PROJECT_NAME})
