if (TARGET tinyusb_device)
    add_executable(whetstone
        whetstone.c
    )

    # pull in common dependencies
    target_link_libraries(whetstone pico_stdlib)
    # pico_set_binary_type(whetstone no_flash)

    # enable usb output, disable uart output
    pico_enable_stdio_usb(whetstone 1)
    pico_enable_stdio_uart(whetstone 0)

    # create map/bin/hex file etc.
    pico_add_extra_outputs(whetstone)

    # add url via pico_set_program_url
    example_auto_set_url(whetstone)
elseif(PICO_ON_DEVICE)
    message(WARNING "not building whetstone because TinyUSB submodule is not initialized in the SDK")
endif()