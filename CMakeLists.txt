CMAKE_MINIMUM_REQUIRED(VERSION 3.1)

PROJECT(SBS VERSION 2020.0602 LANGUAGES CXX)

INCLUDE(FindPkgConfig)

PKG_SEARCH_MODULE(SDL2 REQUIRED sdl2)
PKG_SEARCH_MODULE(SDL2IMAGE REQUIRED SDL2_image>=2.0.0)

ADD_EXECUTABLE(SBS Source/Main.cpp)
SET_TARGET_PROPERTIES(SBS PROPERTIES CXX_STANDARD 17)
TARGET_INCLUDE_DIRECTORIES(SBS PRIVATE ${SDL2_INCLUDE_DIRS})
TARGET_INCLUDE_DIRECTORIES(SBS PRIVATE ${SDL2IMAGE_INCLUDE_DIRS})
TARGET_LINK_LIBRARIES(SBS ${SDL2_LIBRARIES})
TARGET_LINK_LIBRARIES(SBS ${SDL2IMAGE_LIBRARIES})

FILE(COPY ${CMAKE_CURRENT_SOURCE_DIR}/Sprite/BrogueFont5.png DESTINATION ${CMAKE_CURRENT_BINARY_DIR}/)