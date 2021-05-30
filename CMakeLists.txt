cmake_minimum_required(VERSION 3.16)
project(peparser)
set(CMAKE_CXX_STANDARD 14)

set(CMAKE_MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")
set(Boost_USE_STATIC_LIBS ON)
set(Boost_USE_STATIC_RUNTIME ON)

find_package(OpenSSL REQUIRED)
find_package(Boost REQUIRED COMPONENTS program_options filesystem REQUIRED)

add_executable(peparser
    actions.cpp actions.h
    activationcontext.cpp activationcontext.h
    block.cpp block.h
    debugdirectory.h
    dependencycheck.cpp dependencycheck.h
    etoken.cpp etoken.h
    main.cpp
    peparser.cpp peparser.h
    resourcepath.cpp resourcepath.h
    resourcetable.cpp resourcetable.h
    signer.cpp signer.h
    versionstring.cpp versionstring.h
    widestring.cpp widestring.h
    json/json.cpp json/json.h)

include_directories(${Boost_INCLUDE_DIRS})
target_link_libraries(peparser PRIVATE OpenSSL::SSL OpenSSL::Crypto ${Boost_LIBRARIES})
