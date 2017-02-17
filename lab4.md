Root
-------------
    
    cmake_minimum_required (VERSION 2.6)
    project (Tutorial)
     
    # The version number.
    set (Tutorial_VERSION_MAJOR 1)
    set (Tutorial_VERSION_MINOR 0)
     
    # should we use our own math functions
    option(USE_MYMATH 
      "Use tutorial provided math implementation" ON)
     
    # configure a header file to pass some of the CMake settings
    # to the source code
    configure_file (
      "${PROJECT_SOURCE_DIR}/TutorialConfig.h.in"
      "${PROJECT_BINARY_DIR}/TutorialConfig.h"
      )
     
    # add the binary tree to the search path for include files
    # so that we will find TutorialConfig.h
    include_directories ("${PROJECT_BINARY_DIR}")
     
    # add the executable
    add_executable (Tutorial tutorial.cpp)

![Part 1](images/lab4part2.png)

Root
-------------
    
    cmake_minimum_required (VERSION 2.6)
    project (Tutorial)
     
    # The version number.
    set (Tutorial_VERSION_MAJOR 1)
    set (Tutorial_VERSION_MINOR 0)
     
    # should we use our own math functions
    option(USE_MYMATH 
      "Use tutorial provided math implementation" ON)
     
    # configure a header file to pass some of the CMake settings
    # to the source code
    configure_file (
      "${PROJECT_SOURCE_DIR}/TutorialConfig.h.in"
      "${PROJECT_BINARY_DIR}/TutorialConfig.h"
      )
     
    # add the binary tree to the search path for include files
    # so that we will find TutorialConfig.h
    include_directories ("${PROJECT_BINARY_DIR}")
     
    # add the MathFunctions library?
    if (USE_MYMATH)
      include_directories ("${PROJECT_SOURCE_DIR}/MathFunctions")
      add_subdirectory (MathFunctions)
      set (EXTRA_LIBS ${EXTRA_LIBS} MathFunctions)
    endif (USE_MYMATH)
     
    # add the executable
    add_executable (Tutorial tutorial.cpp)
    target_link_libraries (Tutorial  ${EXTRA_LIBS})

MathFunctions
-------------

    # add the main library
    add_library(MathFunctions mysqrt.cpp)

![Part 2](images/lab4part3.png)

Root
-------------
    
    cmake_minimum_required (VERSION 2.6)
    project (Tutorial)
    include(CTest)
     
    # The version number.
    set (Tutorial_VERSION_MAJOR 1)
    set (Tutorial_VERSION_MINOR 0)
     
    # should we use our own math functions
    option(USE_MYMATH 
      "Use tutorial provided math implementation" ON)
     
    # configure a header file to pass some of the CMake settings
    # to the source code
    configure_file (
      "${PROJECT_SOURCE_DIR}/TutorialConfig.h.in"
      "${PROJECT_BINARY_DIR}/TutorialConfig.h"
      )
     
    # add the binary tree to the search path for include files
    # so that we will find TutorialConfig.h
    include_directories ("${PROJECT_BINARY_DIR}")
     
    # add the MathFunctions library?
    if (USE_MYMATH)
      include_directories ("${PROJECT_SOURCE_DIR}/MathFunctions")
      add_subdirectory (MathFunctions)
      set (EXTRA_LIBS ${EXTRA_LIBS} MathFunctions)
    endif (USE_MYMATH)
     
    # add the executable
    add_executable (Tutorial tutorial.cpp)
    target_link_libraries (Tutorial  ${EXTRA_LIBS})
     
    # add the install targets
    install (TARGETS Tutorial DESTINATION bin)
    install (FILES "${PROJECT_BINARY_DIR}/TutorialConfig.h"        
             DESTINATION include)
     
    # does the application run
    add_test (TutorialRuns Tutorial 25)
     
    # does the usage message work?
    add_test (TutorialUsage Tutorial)
    set_tests_properties (TutorialUsage
      PROPERTIES 
      PASS_REGULAR_EXPRESSION "Usage:.*number"
      )
     
     
    #define a macro to simplify adding tests
    macro (do_test arg result)
      add_test (TutorialComp${arg} Tutorial ${arg})
      set_tests_properties (TutorialComp${arg}
        PROPERTIES PASS_REGULAR_EXPRESSION ${result}
        )
    endmacro (do_test)
     
    # do a bunch of result based tests
    do_test (4 "4 is 2")
    do_test (9 "9 is 3")
    do_test (5 "5 is 2.236")
    do_test (7 "7 is 2.645")
    do_test (25 "25 is 5")
    do_test (-25 "-25 is 0")
    do_test (0.0001 "0.0001 is 0.01")

MathFunctions
-------------
     
    # add the main library
    add_library(MathFunctions mysqrt.cpp)
     
    install (TARGETS MathFunctions DESTINATION bin)
    install (FILES MathFunctions.h DESTINATION include)

![Part 3](images/lab4part4.png)

Root
-------------
    
    cmake_minimum_required (VERSION 2.6)
    project (Tutorial)
    include(CTest)
     
    # The version number.
    set (Tutorial_VERSION_MAJOR 1)
    set (Tutorial_VERSION_MINOR 0)
     
    # does this system provide the log and exp functions?
    include (${CMAKE_ROOT}/Modules/CheckFunctionExists.cmake)
     
    check_function_exists (log HAVE_LOG)
    check_function_exists (exp HAVE_EXP)
     
    # should we use our own math functions
    option(USE_MYMATH 
      "Use tutorial provided math implementation" ON)
     
    # configure a header file to pass some of the CMake settings
    # to the source code
    configure_file (
      "${PROJECT_SOURCE_DIR}/TutorialConfig.h.in"
      "${PROJECT_BINARY_DIR}/TutorialConfig.h"
      )
     
    # add the binary tree to the search path for include files
    # so that we will find TutorialConfig.h
    include_directories ("${PROJECT_BINARY_DIR}")
     
    # add the MathFunctions library?
    if (USE_MYMATH)
      include_directories ("${PROJECT_SOURCE_DIR}/MathFunctions")
      add_subdirectory (MathFunctions)
      set (EXTRA_LIBS ${EXTRA_LIBS} MathFunctions)
    endif (USE_MYMATH)
     
    # add the executable
    add_executable (Tutorial tutorial.cpp)
    target_link_libraries (Tutorial  ${EXTRA_LIBS})
     
    # add the install targets
    install (TARGETS Tutorial DESTINATION bin)
    install (FILES "${PROJECT_BINARY_DIR}/TutorialConfig.h"        
             DESTINATION include)
     
    # does the application run
    add_test (TutorialRuns Tutorial 25)
     
    # does the usage message work?
    add_test (TutorialUsage Tutorial)
    set_tests_properties (TutorialUsage
      PROPERTIES 
      PASS_REGULAR_EXPRESSION "Usage:.*number"
      )
     
     
    #define a macro to simplify adding tests
    macro (do_test arg result)
      add_test (TutorialComp${arg} Tutorial ${arg})
      set_tests_properties (TutorialComp${arg}
        PROPERTIES PASS_REGULAR_EXPRESSION ${result}
        )
    endmacro (do_test)
     
    # do a bunch of result based tests
    do_test (4 "4 is 2")
    do_test (9 "9 is 3")
    do_test (5 "5 is 2.236")
    do_test (7 "7 is 2.645")
    do_test (25 "25 is 5")
    do_test (-25 "-25 is 0")
    do_test (0.0001 "0.0001 is 0.01")

MathFunctions
-------------

    # add the main library
    add_library(MathFunctions mysqrt.cpp)
     
    install (TARGETS MathFunctions DESTINATION bin)
    install (FILES MathFunctions.h DESTINATION include)

![Part 4](images/lab4part4.png)

Root
-------------
    
    cmake_minimum_required (VERSION 2.6)
    project (Tutorial)
    include(CTest)
     
    # The version number.
    set (Tutorial_VERSION_MAJOR 1)
    set (Tutorial_VERSION_MINOR 0)
     
    # does this system provide the log and exp functions?
    include (${CMAKE_ROOT}/Modules/CheckFunctionExists.cmake)
     
    check_function_exists (log HAVE_LOG)
    check_function_exists (exp HAVE_EXP)
     
    # should we use our own math functions
    option(USE_MYMATH 
      "Use tutorial provided math implementation" ON)
     
    # configure a header file to pass some of the CMake settings
    # to the source code
    configure_file (
      "${PROJECT_SOURCE_DIR}/TutorialConfig.h.in"
      "${PROJECT_BINARY_DIR}/TutorialConfig.h"
      )
     
    # add the binary tree to the search path for include files
    # so that we will find TutorialConfig.h
    include_directories ("${PROJECT_BINARY_DIR}")
     
    # add the MathFunctions library?
    if (USE_MYMATH)
      include_directories ("${PROJECT_SOURCE_DIR}/MathFunctions")
      add_subdirectory (MathFunctions)
      set (EXTRA_LIBS ${EXTRA_LIBS} MathFunctions)
    endif (USE_MYMATH)
     
    # add the executable
    add_executable (Tutorial tutorial.cpp)
    target_link_libraries (Tutorial  ${EXTRA_LIBS})
     
    # add the install targets
    install (TARGETS Tutorial DESTINATION bin)
    install (FILES "${PROJECT_BINARY_DIR}/TutorialConfig.h"        
             DESTINATION include)
     
    # does the application run
    add_test (TutorialRuns Tutorial 25)
     
    # does the usage message work?
    add_test (TutorialUsage Tutorial)
    set_tests_properties (TutorialUsage
      PROPERTIES 
      PASS_REGULAR_EXPRESSION "Usage:.*number"
      )
     
     
    #define a macro to simplify adding tests
    macro (do_test arg result)
      add_test (TutorialComp${arg} Tutorial ${arg})
      set_tests_properties (TutorialComp${arg}
        PROPERTIES PASS_REGULAR_EXPRESSION ${result}
        )
    endmacro (do_test)
     
    # do a bunch of result based tests
    do_test (4 "4 is 2")
    do_test (9 "9 is 3")
    do_test (5 "5 is 2.236")
    do_test (7 "7 is 2.645")
    do_test (25 "25 is 5")
    do_test (-25 "-25 is 0")
    do_test (0.0001 "0.0001 is 0.01")

MathFunctions
-------------

    # first we add the executable that generates the table
    add_executable(MakeTable MakeTable.cpp)
    # add the command to generate the source code
    add_custom_command (
      OUTPUT ${CMAKE_CURRENT_BINARY_DIR}/Table.h
      DEPENDS MakeTable
      COMMAND MakeTable ${CMAKE_CURRENT_BINARY_DIR}/Table.h
      )
    # add the binary tree directory to the search path 
    # for include files
    include_directories( ${CMAKE_CURRENT_BINARY_DIR} )
     
    # add the main library
    add_library(MathFunctions mysqrt.cpp ${CMAKE_CURRENT_BINARY_DIR}/Table.h)
     
    install (TARGETS MathFunctions DESTINATION bin)
    install (FILES MathFunctions.h DESTINATION include)

![Part 5](images/lab4part5.png)