set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wno-error -Wno-unused-parameter")
get_property(dialect_libs GLOBAL PROPERTY MLIR_DIALECT_LIBS)

add_flang_library(FortranLower
  ComplexExpr.cpp
  ConvertType.cpp
  DoLoopHelper.cpp
  Mangler.cpp
  OpenMP.cpp
  PFTBuilder.cpp

  DEPENDS
  FIROptimizer
  ${dialect_libs}

  LINK_LIBS
  FIROptimizer
  ${dialect_libs}
  MLIRAffineToStandard
  MLIRLLVMIR
  MLIRSCFToStandard
  MLIRStandardOps

  LINK_COMPONENTS
  Support
)
