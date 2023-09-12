# Copyright (c) 2020 The ZMK Contributors
# SPDX-License-Identifier: MIT

if(CONFIG_ZMK_DISPLAY)
  target_sources_ifdef(CONFIG_CUSTOM_WIDGET_BONGO_CAT app PRIVATE bongo_cat.c)
endif()

zephyr_library()

if(CONFIG_ZMK_DISPLAY)
  if(CONFIG_CUSTOM_WIDGET_BONGO_CAT)
    zephyr_library_sources(bongo_img.c)
  endif()
endif()

zephyr_library_include_directories(${ZEPHYR_LVGL_MODULE_DIR})
zephyr_library_include_directories(${ZEPHYR_BASE}/lib/gui/lvgl/)
zephyr_library_sources(${ZEPHYR_BASE}/misc/empty_file.c)
zephyr_library_include_directories(${CMAKE_SOURCE_DIR}/include)
zephyr_library_include_directories(${ZEPHYR_BASE}/drivers)

target_sources_ifdef(CONFIG_ZMK_WIDGET_BATTERY_STATUS app PRIVATE battery_status.c)
target_sources_ifdef(CONFIG_ZMK_WIDGET_OUTPUT_STATUS app PRIVATE output_status.c)
target_sources_ifdef(CONFIG_ZMK_WIDGET_PERIPHERAL_STATUS app PRIVATE peripheral_status.c)
target_sources_ifdef(CONFIG_ZMK_WIDGET_LAYER_STATUS app PRIVATE layer_status.c)
target_sources_ifdef(CONFIG_ZMK_WIDGET_WPM_STATUS app PRIVATE wpm_status.c)
target_sources_ifdef(CONFIG_CUSTOM_WIDGET_BONGO_CAT app PRIVATE bongo_cat.c)
target_sources_ifdef(CONFIG_CUSTOM_WIDGET_BONGO_CAT app PRIVATE bongo_img.c)
