idf_component_register(SRCS "hello_world_main.cpp"
                       PRIV_REQUIRES spi_flash
                       INCLUDE_DIRS "")

target_link_libraries(${COMPONENT_LIB} # __idf_main
    PUBLIC
        cib
)
