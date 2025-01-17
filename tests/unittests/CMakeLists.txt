# SPDX-FileCopyrightText: 2021 Philipp Basler, Margarete Mühlleitner and Jonas
# Müller
#
# SPDX-License-Identifier: GPL-3.0-or-later

set(TESTDIR ${CMAKE_CURRENT_SOURCE_DIR})

file(GLOB SOURCE_FILES "Test-*.cpp" CONFIURE_DEPENDS)
add_executable(GenericTests ${SOURCE_FILES})
target_link_libraries(
  GenericTests
  PRIVATE Catch2::Catch2WithMain
          CatchEventListener
          Minimizer
          Models
          Utility
          TestCompares
          ThermalFunctions)
target_compile_features(GenericTests PUBLIC cxx_std_14)

include(Catch)
catch_discover_tests(GenericTests)

if(BSMPTCompileBaryo)
  add_subdirectory(baryotests)
endif(BSMPTCompileBaryo)
