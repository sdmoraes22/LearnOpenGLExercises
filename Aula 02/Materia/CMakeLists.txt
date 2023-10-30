cmake_minimum_required(VERSION 3.27.6)
project(OpenGLTutorial)

# set(SOURCES main.cpp ${CMAKE_SOURCE_DIR}/../../../../../Libs/glad/src/glad.c)
# set(SOURCES mainVertexDiffColors.cpp ${CMAKE_SOURCE_DIR}/../../../../../Libs/glad/src/glad.c)
set(SOURCES mainExternalShaders.cpp ${CMAKE_SOURCE_DIR}/../../../../../Libs/glad/src/glad.c)
add_executable(OpenGLTutorial ${SOURCES})
target_include_directories(OpenGLTutorial PRIVATE ${CMAKE_SOURCE_DIR}/../../../../../Libs/glad/include/)
target_sources(OpenGLTutorial PRIVATE ${CMAKE_SOURCE_DIR}/../../../../../Libs/glad/src/)
target_include_directories(OpenGLTutorial PRIVATE ${CMAKE_SOURCE_DIR}/../../../../../Libs/glfw-3.3.8.bin.WIN64/include/)
target_include_directories(OpenGLTutorial PRIVATE ${CMAKE_SOURCE_DIR}/learnopengl/)
target_link_directories(OpenGLTutorial PRIVATE ${CMAKE_SOURCE_DIR}/../../../../../Libs/glfw-3.3.8.bin.WIN64/lib-mingw-w64/)
target_link_libraries(OpenGLTutorial glfw3)

add_custom_target(copy_resources ALL 
    COMMAND ${CMAKE_COMMAND} -E copy_directory
    ${PROJECT_SOURCE_DIR}/Shaders
    ${PROJECT_BINARY_DIR}/Shaders)
