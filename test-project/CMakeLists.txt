add_executable(test_project
    main.cpp
)

# Include and link directories from sysroot based on example project
target_include_directories(test_project
    PUBLIC
        ${SYSROOT_PATH}/usr/include
)

target_link_directories(test_project
    PUBLIC
        ${SYSROOT}/lib
        ${SYSROOT}/usr/lib
)

# Add custom command to "load" with SCP
add_custom_target( 
    load-project-exe
    COMMAND sshpass -p "milkv" scp test_project root@192.168.42.1:/root/
    DEPENDS test_project
    WORKING_DIRECTORY ${CMAKE_BUILD_DIR}
    VERBATIM USES_TERMINAL
    COMMENT "Loading application to 192.168.42.1:/root/"
)