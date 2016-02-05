cmake_minimum_required(VERSION 2.8.5 FATAL_ERROR)
if(POLICY CMP0025)
  cmake_policy(SET CMP0025 NEW) # CMake 3.0
endif()
if(POLICY CMP0053)
  cmake_policy(SET CMP0053 NEW) # CMake 3.1
endif()

project (VTKPointCloudTest)

set(CMAKE_MACOSX_RPATH 1)

if(NOT DEFINED VTK_RENDERING_BACKEND)
  set(VTK_RENDERING_BACKEND "OpenGL")
endif()

find_package(VTK 6.3 COMPONENTS
  vtkFiltersExtraction
  vtkFiltersFlowPaths
  vtkFiltersGeometry
  vtkImagingMath
  vtkzlib
  vtkFiltersSources
  vtkInteractionStyle
  vtkRendering${VTK_RENDERING_BACKEND}
  vtkPointCloud
)

include(${VTK_USE_FILE})

add_executable(VTKPointCloudTest MACOSX_BUNDLE VTKPointCloudTest.cxx)
target_link_libraries(VTKPointCloudTest ${VTK_LIBRARIES})
