To setup project on your own machine:


1. git clone --recurse-submodules <THIS_REPO_URL>

2. cd glfw-starter

3. cmake -S . -B build

4. cmake --build build --config Release



To run main.cpp for the first time:


1. Navigate to root folder of project

2. mkdir build

3. cd build

4. cmake ..
   
5. cmake --build . --config Release

6. cd Release

7. ./glfw_starter.exe



To run main.cpp afterwards:


1. cd build

2.  cmake --build . --config Release

3.  cd Release

4.  .\glfw_starter.exe
