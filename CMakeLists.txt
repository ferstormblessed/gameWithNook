cmake_minimum_required(VERSION 3.16)
project(GameWithNook VERSION 1.0.0 LANGUAGES CXX)

include(FetchContent)

FetchContent_Declare(
        Nook
        GIT_REPOSITORY https://github.com/ferstormblessed/NookLibrary
        GIT_TAG main # o la etiqueta que desees usar
)

FetchContent_MakeAvailable(Nook)

# Create an executable target
add_executable(main main.cpp)

# Include directories for Nook
target_include_directories(main PRIVATE ${Nook_SOURCE_DIR}/include)

# Link Nook and other dependencies
target_link_libraries(main PRIVATE NOOK sfml-graphics sfml-audio ImGui-SFML::ImGui-SFML box2d)

# Agregar la ruta de búsqueda para la biblioteca Nook
link_directories(${Nook_BINARY_DIR})