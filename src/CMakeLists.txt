cmake_minimum_required( VERSION 2.6 )

set( BIN doom2d )
project( ${BIN} )

set( SOURCE_ROOT ../src )

find_package(SDL2 REQUIRED)
find_package(SDL2_mixer REQUIRED)

aux_source_directory( ${SOURCE_ROOT} SOURCES )

include_directories( "${SOURCE_ROOT}"
         "${SDL2_INCLUDE_DIR}" )
         #"${SDL2_MIXER_INCLUDE_DIRS}")
#        "${SDL2_INCLUDE_DIR}"
#        "${SDL2_MIXER_INCLUDE_DIR}" )

set( INSTALL_PATH /usr/local/bin/ )

set( CMAKE_CXX_FLAGS "-O1 -Wall" ) 

add_executable( ${BIN} ${SOURCES} )

set(CMAKE_BUILD_TYPE Debug)


target_link_libraries( ${BIN} "-lSDL2" "-lSDL2_mixer" )

install( TARGETS ${BIN} DESTINATION ${INSTALL_PATH} )
