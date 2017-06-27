#Copyright (c) Microsoft. All rights reserved.
#Licensed under the MIT license. See LICENSE file in the project root for full license information.

# Please add below statement in CMakeLists.txt of samples folder

# use http rest api module
add_subdirectory(httprestapi_sample)

# use ble filter extention
if(${enable_ble_module} AND LINUX)
    add_subdirectory(ble_filter_gateway)
endif()

if(WIN32)
    add_subdirectory(filter_sample)
endif()
