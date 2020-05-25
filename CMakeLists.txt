cmake_minimum_required(VERSION 3.15)

project(oscar_iso8583 LANGUAGES C)

add_library(iso8583lib STATIC
    dl_c_iso8583_v0_0_3/dl_iso8583.c
    dl_c_iso8583_v0_0_3/dl_iso8583.h
    dl_c_iso8583_v0_0_3/dl_iso8583_common.c
    dl_c_iso8583_v0_0_3/dl_iso8583_common.h
    dl_c_iso8583_v0_0_3/dl_iso8583_defs_1987.c
    dl_c_iso8583_v0_0_3/dl_iso8583_defs_1987.h
    dl_c_iso8583_v0_0_3/dl_iso8583_defs_1993.c
    dl_c_iso8583_v0_0_3/dl_iso8583_defs_1993.h
    dl_c_iso8583_v0_0_3/dl_iso8583_fields.c
    dl_c_iso8583_v0_0_3/dl_iso8583_fields.h
)

add_library(commonlib STATIC
    dl_c_common_v0_0_2/dl_base.h
    dl_c_common_v0_0_2/dl_err.h
    dl_c_common_v0_0_2/dl_mem.c
    dl_c_common_v0_0_2/dl_mem.h
    dl_c_common_v0_0_2/dl_output.c
    dl_c_common_v0_0_2/dl_output.h
    dl_c_common_v0_0_2/dl_str.c
    dl_c_common_v0_0_2/dl_str.h
    dl_c_common_v0_0_2/dl_time.c
    dl_c_common_v0_0_2/dl_time.h
    dl_c_common_v0_0_2/dl_timer.c
    dl_c_common_v0_0_2/dl_timer.h
)

target_link_libraries(iso8583lib commonlib)
target_link_libraries(commonlib iso8583lib)


target_include_directories(iso8583lib PUBLIC dl_c_iso8583_v0_0_3)
target_include_directories(commonlib PUBLIC dl_c_common_v0_0_2)

#add_executable(demo demo.c)
#target_link_libraries(demo PUBLIC iso8583lib commonlib)
