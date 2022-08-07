cmake_minimum_required(VERSION 3.0)
project(GTA-SA-PSP ASM C CXX)
SET(CMAKE_SYSTEM_NAME "Generic")

SET(CMAKE_FIND_ROOT_PATH "C:\\pspsdk\\bin")

SET(CMAKE_C_COMPILER psp-gcc)
SET(CMAKE_CXX_COMPILER psp-g++)
SET(CMAKE_MAKE_PROGRAM make)
SET(CMAKE_RC_COMPILER psp-ar)

add_executable(GTA-SA-PSP
  main.c
  openal_patch.c
  opengl_patch.c
  memcpy_neon.S
)

if(PLATFORM_PSP)

    create_pbp_file(
        TARGET GTA-SA
        ICON_PATH NULL
        PREVIEW_PATH NULL
        TITLE Grand Theft Auto San Andreas
        BUILD_PRX
    )

    target_link_libraries(GTA-SA-PSP pspdebug pspdisplay pspge)
endif()