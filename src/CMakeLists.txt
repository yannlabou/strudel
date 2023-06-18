add_executable(echo echo.cpp)
target_link_libraries(echo PRIVATE compiler-warnings)
target_link_libraries(echo PRIVATE fmt::fmt)

set_target_properties(echo PROPERTIES RUNTIME_OUTPUT_DIRECTORY "${PROJECT_BINARY_DIR}/bin")