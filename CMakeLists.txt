project(kinect-playground CXX C)
cmake_minimum_required(VERSION 2.8)

find_package(PkgConfig REQUIRED)

pkg_check_modules(FREENECT libfreenect REQUIRED)
include_directories(${FREENECT_INCLUDE_DIRS})

find_package(OpenGL REQUIRED)
include_directories(${OPENGL_INCLUDE_DIR})

find_package(GLUT REQUIRED)
include_directories(${GLUT_INCLUDE_DIR})

add_executable(glview glview.cpp)
target_link_libraries(glview
	${FREENECT_LIBRARIES}
	${OPENGL_LIBRARIES}
	${GLUT_LIBRARIES}
	pthread
)
