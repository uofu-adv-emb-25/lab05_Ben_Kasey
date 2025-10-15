add_compile_definitions(
    DELAY_MS=100
    IN_PIN=6
    OUT_PIN=7)

# This is the main binary. List your C files here.
add_executable(gpio_interrupt
    gpio_interrupt.c
    )

# Modify the below lines to enable/disable output over UART/USB.
# These are mutually exclusive, only set one.
pico_enable_stdio_uart(gpio_interrupt 0)
pico_enable_stdio_usb(gpio_interrupt 1)

# Add the libraries to the build
target_link_libraries(gpio_interrupt PRIVATE
  pico_stdlib
  pico_multicore
  pico_async_context_freertos
  FreeRTOS-Kernel-Heap4
  hardware_rtc
  pico_cyw43_arch_none
)

# The CYW43 is the Wifi/Bluetooth module. If the board is set to pico_w, this
# variable will be set and the wireless libraries added.
if(PICO_CYW43_SUPPORTED)
    # For led support on pico_w
    target_link_libraries(gpio_interrupt PRIVATE
        pico_cyw43_arch_none
    )
endif()

# Another pico macro which generates the uf2 file in addition to the elf
pico_add_extra_outputs(gpio_interrupt)

find_program(OPENOCD openocd)
find_program(PICOTOOL picotool)

add_custom_target(flash ${PICOTOOL} load -f $<TARGET_FILE:hello_freertos> DEPENDS gpio_interrupt)

add_custom_target(openocd_flash ${OPENOCD} -s ${OPENOCD_PATH} -f interface/cmsis-dap.cfg -f target/rp2040.cfg -c 'adapter speed 5000; program "$<TARGET_FILE:gpio_interrupt>" verify reset exit' DEPENDS gpio_interrupt)

# rtc
add_executable(rtc
    rtc.c
    )

pico_enable_stdio_uart(rtc 0)
pico_enable_stdio_usb(rtc 1)

target_link_libraries(rtc PRIVATE
  pico_stdlib
  pico_multicore
  pico_async_context_freertos
  FreeRTOS-Kernel-Heap4
  hardware_rtc
  pico_cyw43_arch_none
)

pico_add_extra_outputs(rtc)

find_program(OPENOCD openocd)
find_program(PICOTOOL picotool)

add_custom_target(flash ${PICOTOOL} load -f $<TARGET_FILE:hello_freertos> DEPENDS rtc)

add_custom_target(openocd_flash ${OPENOCD} -s ${OPENOCD_PATH} -f interface/cmsis-dap.cfg -f target/rp2040.cfg -c 'adapter speed 5000; program "$<TARGET_FILE:rtc>" verify reset exit' DEPENDS rtc)

# sleep
add_executable(sleep
    sleep.c
    )

pico_enable_stdio_uart(sleep 0)
pico_enable_stdio_usb(sleep 1)

target_link_libraries(sleep PRIVATE
  pico_stdlib
  pico_multicore
  pico_async_context_freertos
  FreeRTOS-Kernel-Heap4
  hardware_rtc
  pico_cyw43_arch_none
)

pico_add_extra_outputs(sleep)

find_program(OPENOCD openocd)
find_program(PICOTOOL picotool)

add_custom_target(flash ${PICOTOOL} load -f $<TARGET_FILE:hello_freertos> DEPENDS sleep)

add_custom_target(openocd_flash ${OPENOCD} -s ${OPENOCD_PATH} -f interface/cmsis-dap.cfg -f target/rp2040.cfg -c 'adapter speed 5000; program "$<TARGET_FILE:sleep>" verify reset exit' DEPENDS sleep)

# task_delay
add_executable(task_delay
    task_delay.c
    )

pico_enable_stdio_uart(task_delay 0)
pico_enable_stdio_usb(task_delay 1)

target_link_libraries(task_delay PRIVATE
  pico_stdlib
  pico_multicore
  pico_async_context_freertos
  FreeRTOS-Kernel-Heap4
  hardware_rtc
  pico_cyw43_arch_none
)

pico_add_extra_outputs(task_delay)

find_program(OPENOCD openocd)
find_program(PICOTOOL picotool)

add_custom_target(flash ${PICOTOOL} load -f $<TARGET_FILE:hello_freertos> DEPENDS task_delay)

add_custom_target(openocd_flash ${OPENOCD} -s ${OPENOCD_PATH} -f interface/cmsis-dap.cfg -f target/rp2040.cfg -c 'adapter speed 5000; program "$<TARGET_FILE:task_delay>" verify reset exit' DEPENDS task_delay)

# timer
add_executable(timer
    timer.c
    )

pico_enable_stdio_uart(timer 0)
pico_enable_stdio_usb(timer 1)

target_link_libraries(timer PRIVATE
  pico_stdlib
  pico_multicore
  pico_async_context_freertos
  FreeRTOS-Kernel-Heap4
  hardware_rtc
  pico_cyw43_arch_none
)

pico_add_extra_outputs(timer)

find_program(OPENOCD openocd)
find_program(PICOTOOL picotool)

add_custom_target(flash ${PICOTOOL} load -f $<TARGET_FILE:hello_freertos> DEPENDS timer)

add_custom_target(openocd_flash ${OPENOCD} -s ${OPENOCD_PATH} -f interface/cmsis-dap.cfg -f target/rp2040.cfg -c 'adapter speed 5000; program "$<TARGET_FILE:timer>" verify reset exit' DEPENDS timer)