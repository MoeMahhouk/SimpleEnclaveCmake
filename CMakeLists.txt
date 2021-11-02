cmake_minimum_required(VERSION 3.10)
project(blockchain "C" "CXX")

include(cmake/FindSGXSDK.cmake)
include(cmake/ConfigSGX.cmake)

set(COMMON_INCLUDE_DIR "${CMAKE_CURRENT_SOURCE_DIR}/Include")

set(ENCLAVE_LIB_NAME            SimpleEnclave)
set(SIGNED_ENCLAVE_NAME         SimpleEnclave.signed.so)
set(APP_NAME                    SimpleSGXApp)
#set(Security_Link_Flags			    "-Wl,-z,noexecstack -Wl,-z,relro -Wl,-z,now -pie")


add_definitions(-DENCLAVE_FILENAME="${SIGNED_ENCLAVE_NAME}")



add_subdirectory(Enclave)
add_subdirectory(App)