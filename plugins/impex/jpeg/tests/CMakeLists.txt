include_directories(${CMAKE_SOURCE_DIR}/sdk/tests)
include(KritaAddBrokenUnitTest)

macro_add_unittest_definitions()

if (APPLE)

    krita_add_broken_unit_tests(
        kis_jpeg_test.cpp
        LINK_LIBRARIES kritametadata kritaui Qt5::Test
        NAME_PREFIX "plugins-impex-"
        TARGET_NAMES_VAR BROKEN_TESTS
        ${MACOS_GUI_TEST}
    )

    macos_test_fixrpath(${BROKEN_TESTS})

else (APPLE)
    ecm_add_test(
        kis_jpeg_test.cpp
        TEST_NAME kis_jpeg_test
        LINK_LIBRARIES kritametadata kritaui Qt5::Test
        NAME_PREFIX "plugins-impex-"
        )

endif()
