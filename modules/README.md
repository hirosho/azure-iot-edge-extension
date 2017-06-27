# Extension Modules for Azure IoT Edge SDK
Extension modules for [Azure IoT Edge SDK](http:/github.com/azure/iot-edge) 
When you use these module, copy the whole contens in each folder to modules directory which is cloned from SDK repository and add statement in CMakeLists.txt from this folder's CMakeLists.txt. 
## httprestapi 
This module provide HTTP REST API service capablity using CPP REST SDK. 

## filter 
This module is extention of ble_gateway sample. By use this module and resolvers raw data from ble module is converted to physical quantity and is presented as JSON format. 
Please see [ble_filter_gateway sample](../samples/ble_filter_gateway/README.md). 
