# ACA_face-detector
Simple face-detector program using CMake, vcpkg and OpenCV library. Original example https://www.geeksforgeeks.org/opencv-c-program-face-detection/

## build
```
$ cmake -B [build directory] -S . -DCMAKE_TOOLCHAIN_FILE=[path to vcpkg]/scripts/buildsystems/vcpkg.cmake
$ cmake --build [build directory]
```

