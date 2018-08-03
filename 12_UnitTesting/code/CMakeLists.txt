CMAKE_MINIMUM_REQUIRED(VERSION 2.8)

SET( PROJECT_NAME UnitTesting_Tutorial )


IF( APPLE )
# requires 'brew install libomp'
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Xpreprocessor -fopenmp -lomp")
ENDIF( APPLE )

# Set project name 
PROJECT( ${PROJECT_NAME} )
SET(EXE_NAME "${PROJECT_NAME}" CACHE STRING "Executable name" FORCE)
 
#Find libraries
FIND_PACKAGE( ITK REQUIRED )
INCLUDE( ${ITK_USE_FILE} )

# Add sources to executable
ADD_EXECUTABLE(
  ${EXE_NAME} 
  ${PROJECT_SOURCE_DIR}/src/BasicApp.h
  ${PROJECT_SOURCE_DIR}/src/cbicaITKWriteImage.h
  ${PROJECT_SOURCE_DIR}/src/cbicaUtilities.h
  ${PROJECT_SOURCE_DIR}/src/cbicaUtilities.cpp
  ${PROJECT_SOURCE_DIR}/src/cbicaCmdParser.h
  ${PROJECT_SOURCE_DIR}/src/cbicaCmdParser.cpp
  ${PROJECT_SOURCE_DIR}/src/main.cxx
)

# Link the libraries to be used
TARGET_LINK_LIBRARIES(
  ${EXE_NAME}
  ${ITK_LIBRARIES}
)

ENABLE_TESTING()
ADD_SUBDIRECTORY(testing)