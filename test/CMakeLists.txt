# raylib-tmx-test
add_executable(raylib-tmx-test raylib-tmx-test.c)

if(WIN32)
target_compile_options(raylib-tmx-test PRIVATE -Wall)
else()
target_compile_options(raylib-tmx-test PRIVATE -Wall -Wextra -Wconversion -Wsign-conversion)
endif(WIN32)

target_link_libraries(raylib-tmx-test PUBLIC
    raylib
    raylib-tmx
)

# Copy the resources
file(GLOB resources resources/*)
set(test_resources)
list(APPEND test_resources ${resources})
file(COPY ${test_resources} DESTINATION "resources/")

# Set up the test
add_test(NAME raylib-tmx-test COMMAND raylib-tmx-test)
