#  Copyright (c) Microsoft Corporation. All rights reserved.
#  Licensed under the MIT License.

cmake_minimum_required(VERSION 3.20)

project(WolfSSL_HighLevelApp C)

add_executable(${PROJECT_NAME} main.c eventloop_timer_utilities.c)
target_link_libraries(${PROJECT_NAME} applibs gcc_s c wolfssl)
target_compile_definitions(${PROJECT_NAME} PUBLIC -D_GNU_SOURCE)

azsphere_target_add_image_package(${PROJECT_NAME} RESOURCE_FILES "certs/DigiCertGlobalRootG3.crt.pem")
