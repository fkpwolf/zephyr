# SPDX-License-Identifier: Apache-2.0

cmake_minimum_required(VERSION 3.20.0)

find_package(Zephyr REQUIRED HINTS $ENV{ZEPHYR_BASE})
project(bsim_test_security_changed_callback)

add_subdirectory(${ZEPHYR_BASE}/tests/bsim/babblekit babblekit)
target_link_libraries(app PRIVATE babblekit)

target_sources(app PRIVATE
	src/bs_bt_utils.c
	src/central.c
	src/main.c
	src/peripheral.c
)

zephyr_include_directories(
  ${BSIM_COMPONENTS_PATH}/libUtilv1/src/
  ${BSIM_COMPONENTS_PATH}/libPhyComv1/src/
)
