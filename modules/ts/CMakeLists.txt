set(the_description "The ts module")

if(IOS)
  ocv_module_disable(ts)
endif()

if(MINGW)
  set(OPENCV_MODULE_TYPE STATIC)
endif()

set(OPENCV_MODULE_IS_PART_OF_WORLD FALSE)

ocv_add_module(ts opencv_core opencv_features2d)

ocv_glob_module_sources()
ocv_module_include_directories()
ocv_create_module()

if(BUILD_SHARED_LIBS AND NOT MINGW)
  add_definitions(-DGTEST_CREATE_SHARED_LIBRARY=1)
else()
  add_definitions(-DGTEST_CREATE_SHARED_LIBRARY=0)
endif()

ocv_add_precompiled_headers(${the_module})
