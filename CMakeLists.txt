cmake_minimum_required(VERSION 2.8)
# Project Name
PROJECT(gasget_case)

#########################################################
# FIND GLUT
#########################################################
find_package(GLUT REQUIRED)
include_directories(${GLUT_INCLUDE_DIRS})
link_directories(${GLUT_LIBRARY_DIRS})
add_definitions(${GLUT_DEFINITIONS})

#Check if GLUT found, display error if not found
if(NOT GLUT_FOUND)
    message(ERROR " GLUT not found!")
endif(NOT GLUT_FOUND)

#########################################################
# FIND OPENGL
#########################################################
find_package(OpenGL REQUIRED)
include_directories(${OpenGL_INCLUDE_DIRS})
link_directories(${OpenGL_LIBRARY_DIRS})
add_definitions(${OpenGL_DEFINITIONS})

#Check if OpenGL found, display error if not found
if(NOT OPENGL_FOUND)
    message(ERROR " OPENGL not found!")
endif(NOT OPENGL_FOUND)

#########################################################
# Include Files
#########################################################
add_executable(${PROJECT_NAME}_2d src/2d_s_gasket.cpp)
add_executable(${PROJECT_NAME}_triangle src/recursive_subdivison_s_gas.cpp)
add_executable(${PROJECT_NAME}_tet src/recursive_subdivison_tet_s_gas.cpp)

########################################################
# Linking & stuff
#########################################################

  # create the program "test"
  target_link_libraries(${PROJECT_NAME}_2d ${OPENGL_LIBRARIES} ${GLUT_LIBRARY})
  target_link_libraries(${PROJECT_NAME}_triangle ${OPENGL_LIBRARIES} ${GLUT_LIBRARY})
  target_link_libraries(${PROJECT_NAME}_tet ${OPENGL_LIBRARIES} ${GLUT_LIBRARY})

