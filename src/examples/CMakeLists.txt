add_executable(iris_example iris/iris.cpp)
cuda_add_executable(mnist_example mnist/mnist_ffnn.cu)

foreach(exec iris_example mnist_example)
  target_link_libraries(${exec} marian ${EXT_LIBS})
  cuda_add_cublas_to_target(${exec})
  set_target_properties(${exec} PROPERTIES RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}")
endforeach(exec)
