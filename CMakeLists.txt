cmake_minimum_required(VERSION 3.16)

project(face-detector LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(OpenCV REQUIRED)

add_executable(face-detector main.cpp)

target_link_libraries(face-detector
 PRIVATE
 opencv_core
 opencv_objdetect
 opencv_video
 opencv_videoio
 opencv_highgui)

 # Copy files to build directory
set(copy_source_dir "${CMAKE_SOURCE_DIR}/")
set(copy_dest_dir "${CMAKE_BINARY_DIR}/$<CONFIG>")
set(copy_file_name1 "haarcascade_eye_tree_eyeglasses.xml")
set(copy_file_name2 "haarcascade_frontalcatface.xml")

message(${copy_dest_dir})

add_custom_command(
    TARGET face-detector POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E make_directory ${copy_dest_dir}
)
add_custom_command(
    TARGET face-detector POST_BUILD 
    COMMAND ${CMAKE_COMMAND} -E copy "${copy_source_dir}/${copy_file_name1}" "${copy_dest_dir}/${copy_file_name1}"
    COMMENT "Copying ${copy_file_name1} to build directory")
add_custom_command(
    TARGET face-detector POST_BUILD 
    COMMAND ${CMAKE_COMMAND} -E copy "${copy_source_dir}/${copy_file_name2}" "${copy_dest_dir}/${copy_file_name2}"
    COMMENT "Copying ${copy_file_name2} to build directory")