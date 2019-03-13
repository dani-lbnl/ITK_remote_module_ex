itk_module_test()

set(DanceTests
  itkMinimalStandardRandomVariateGeneratorTest.cxx
  itkNormalDistributionImageSourceTest.cxx
  itkDanceFilterTest.cxx
  )

CreateTestDriver(Dance "${Dance-Test_LIBRARIES}" "${DanceTests}")

itk_add_test(NAME itkMinimalStandardRandomVariateGeneratorTest
  COMMAND DanceTestDriver itkMinimalStandardRandomVariateGeneratorTest
  )

itk_add_test(NAME itkDanceFilterTest
  COMMAND DanceTestDriver
    --compare
    ${ITK_TEST_OUTPUT_DIR}/itkDanceFilterTestOutput.mha
    DATA{Baseline/itkDanceFilterTestOutput.mha}
  itkDanceFilterTest
    ${ITK_TEST_OUTPUT_DIR}/itkDanceFilterTestOutput.mha
  )

itk_add_test(NAME itkNormalDistributionImageSourceTest
  COMMAND DanceTestDriver --without-threads
  --compare
    ${ITK_TEST_OUTPUT_DIR}/itkNormalDistributionImageSourceTestOutput.mha
    DATA{Baseline/itkNormalDistributionImageSourceTestOutput.mha}
  itkNormalDistributionImageSourceTest
    ${ITK_TEST_OUTPUT_DIR}/itkNormalDistributionImageSourceTestOutput.mha
  )
