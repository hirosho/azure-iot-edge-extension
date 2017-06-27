#Copyright (c) Microsoft. All rights reserved.
#Licensed under the MIT license. See LICENSE file in the project root for full license information.

cmake_minimum_required(VERSION 2.8.12)

set(httprestapi_sources
    ./src/main.c
)
if(WIN32)
    set(httprestapi_sources 
        ${httprestapi_sources}
        ./src/httprestapi_win.json
    )
    set_source_files_properties(./src/httprestapi_win.json PROPERTIES HEADER_FILE_ONLY ON)
else()
    set(httprestapi_sources 
        ${httprestapi_sources}
        ./src/httprestapi_lin.json
    )
    set_source_files_properties(./src/httprestapi_lin.json PROPERTIES HEADER_FILE_ONLY ON)
endif()

include_directories(./inc ${IOTHUB_CLIENT_INC_FOLDER})
include_directories(${GW_INC})
include_directories(../../modules/common)

add_executable(httprestapi_sample ${httprestapi_sources})

add_dependencies(httprestapi_sample httprestapi logger)

target_link_libraries(httprestapi_sample gateway nanomsg ${CPPREST_LIBRARIES})
linkSharedUtil(httprestapi_sample)
install_broker(httprestapi_sample ${CMAKE_CURRENT_BINARY_DIR}/$(Configuration) )
copy_gateway_dll(httprestapi_sample ${CMAKE_CURRENT_BINARY_DIR}/$(Configuration) )

add_sample_to_solution(httprestapi_sample)