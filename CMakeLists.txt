cmake_minimum_required(VERSION 3.10)
project(Omnimagnet_Project)
find_package( OpenCV REQUIRED )
add_library(
	omnimagnet
	omnimagnet.cpp
	omnimagnet.hpp
	)
add_library(
	cameratrack
	cameratrack.cpp
	cameratrack.hpp
	)

add_library(
	type
	type.cpp
	type.hpp
	)
add_executable(SystemRun main.cpp)
# INCLUDE_DIRECTORIES("/home/ashkan/Desktop/naghi_C/build/")
INCLUDE_DIRECTORIES(/home/ashkan/eigen/source , /usr/local/lib, /usr/include/spinnaker)

# target_link_libraries(pigi PRIVATE "/home/ashkan/Desktop/naghi_C/build/libghazam.a" )
# target_link_libraries(SystemRun PRIVATE omnimagnet type "/usr/lib/libSpinnaker.so")
target_link_libraries(cameratrack PRIVATE  "/usr/lib/libSpinnaker.so" ${OpenCV_LIBS})
target_link_libraries(SystemRun PRIVATE omnimagnet type  cameratrack "/usr/local/lib/libcomedi.a")
