# Copyright (c) 2023 ARM Limited. All rights reserved.
# SPDX-License-Identifier: Apache-2.0

add_library(mbed-nucleo-l412kb INTERFACE)

target_sources(mbed-nucleo-l412kb
    INTERFACE
        PeripheralPins.c
)

target_include_directories(mbed-nucleo-l412kb
    INTERFACE
        .
)

target_link_libraries(mbed-nucleo-l412kb INTERFACE mbed-stm32l412xb)
