#================================================================================
cmake_minimum_required(VERSION 3.15)
set(CMAKE_TOOLCHAIN_FILE cmake/arm-none-eabi-gcc.cmake)


#================================================================================
project(# LANGUAGES CXX C ASM)
set(DEVICE stm32f407vg)


include(libopencm3)

#include(freertos_kernel)


#================================================================================
add_executable(${PROJECT_NAME}
     src/main.cpp
)

target_link_libraries(${PROJECT_NAME}
     libopencm3
#     freertos_kernel
)


#================================================================================
set(PROG stlink-v2)
string(CONCAT PROG_TARGET ${LOCM3_DEVICE_SERIE} x)

include(oocd_flash_script)

install(CODE ${OOCD_FLASH_SCRIPT})

