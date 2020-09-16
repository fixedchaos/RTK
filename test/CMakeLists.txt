configure_file (${CMAKE_CURRENT_SOURCE_DIR}/rtkTestConfiguration.h.in
  ${RTK_BINARY_DIR}/rtkTestConfiguration.h)

itk_module_test()

# Use sha512 algorithm to generate content link
if(NOT ITK_SOURCE_DIR)
  set(ExternalData_LINK_CONTENT SHA512)
endif()


set(RTKTests
  rtkFDKTest.cxx
  )

CreateTestDriver(RTK "${RTK_LIBRARIES}" "${RTKTests}")

itk_add_test(NAME rtkFDKTestCPU
  COMMAND RTKTestDriver
    rtkFDKTest
    )
