project(ncnnyolox)

cmake_minimum_required(VERSION 3.10)

set(OpenCV_DIR ${CMAKE_SOURCE_DIR}/opencv-mobile-2.4.13.7-android/sdk/native/jni)
find_package(OpenCV REQUIRED core imgproc)

#set(ncnn_DIR ${CMAKE_SOURCE_DIR}/ncnn-20210720-android-vulkan/${ANDROID_ABI}/lib/cmake/ncnn)
set(ncnn_DIR /home/yyang/Archdevel/workspace/sources/ncnn/build-android-aarch64/install/lib/cmake/ncnn)
find_package(ncnn REQUIRED)

add_library(ncnnyolox SHARED yoloxncnn.cpp yolox.cpp ndkcamera.cpp)

target_link_libraries(ncnnyolox ncnn ${OpenCV_LIBS} camera2ndk mediandk)
