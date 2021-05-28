cmake_minimum_required(VERSION 3.16)
project(peparser)
set(CMAKE_CXX_STANDARD 14)

include(conanbuildinfo.cmake)
conan_basic_setup()

add_executable(peparser 
    actions.cpp actions.h
    activationcontext.cpp activationcontext.h
    block.cpp block.h
    debugdirectory.h
    dependencycheck.cpp dependencycheck.h
    etoken.cpp etoken.h
    main.cpp
    peparser.cpp peparser.h
    resource.h
    resourcepath.cpp resourcepath.h
    resourcetable.cpp resourcetable.h
    signer.cpp signer.h
    versionstring.cpp versionstring.h
    widestring.cpp widestring.h
    json/json.cpp json/json.h)

target_link_libraries(peparser PRIVATE ${CONAN_LIBS})