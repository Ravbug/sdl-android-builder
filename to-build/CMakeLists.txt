
cmake_minimum_required(VERSION 3.6)
PROJECT(SDLAndroidBuild)

# https://stackoverflow.com/questions/7787823/cmake-how-to-get-the-name-of-all-subdirectories-of-a-directory
macro(subdirlist result curdir)
  file(GLOB children RELATIVE ${curdir} ${curdir}/*)
  set(dirlist "")
  foreach(child ${children})
    if(IS_DIRECTORY ${curdir}/${child})
      list(APPEND dirlist ${child})
    endif()
  endforeach()
  set(${result} ${dirlist})
endmacro()

subdirlist(SUBDIRS "${CMAKE_CURRENT_LIST_DIR}")
foreach(subdir ${SUBDIRS})
    add_subdirectory("${subdir}")
endforeach()