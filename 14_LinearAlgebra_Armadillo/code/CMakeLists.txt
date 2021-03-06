CMAKE_MINIMUM_REQUIRED(VERSION 2.8)

SET( PROJECT_NAME Armadillo_Tutorial )

# Set project name 
PROJECT( ${PROJECT_NAME} )
 
#Find libraries
FIND_PACKAGE( ITK REQUIRED )
INCLUDE( ${ITK_USE_FILE} )

FIND_PACKAGE( Armadillo REQUIRED )
INCLUDE_DIRECTORIES(${ARMADILLO_INCLUDE_DIRS})

SET( CommonSources
  ${CMAKE_CURRENT_SOURCE_DIR}/src/cbicaITKSafeImageIO.h
  ${CMAKE_CURRENT_SOURCE_DIR}/src/cbicaUtilities.h
  ${CMAKE_CURRENT_SOURCE_DIR}/src/cbicaUtilities.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/src/cbicaCmdParser.h
  ${CMAKE_CURRENT_SOURCE_DIR}/src/cbicaCmdParser.cpp
)

# Add sources to executable
ADD_EXECUTABLE(
  ${PROJECT_NAME}
  ${CMAKE_CURRENT_SOURCE_DIR}/src/main.cxx
  ${CommonSources}
)

# Link the libraries to be used
TARGET_LINK_LIBRARIES(
  ${PROJECT_NAME}
  ${ITK_LIBRARIES}
  ${ARMADILLO_LIBRARIES}
)
