
file(GLOB locale_jsons ${valhalla_SOURCE_DIR}/locales *.json)
add_custom_command(OUTPUT ${CMAKE_CURRENT_BINARY_DIR}/locales.h
  COMMAND ${CMAKE_COMMAND} -DMSVC=${MSVC} -P cmake/Binary2Header.cmake ${valhalla_SOURCE_DIR}/locales/ ${CMAKE_CURRENT_BINARY_DIR}/locales.h --locales
  WORKING_DIRECTORY ${valhalla_SOURCE_DIR}
  COMMENT "Compiling locales/*.json to locales.h"
  DEPENDS ${locale_jsons}
  VERBATIM)

set(headers
    ${CMAKE_CURRENT_BINARY_DIR}/locales.h
    ${valhalla_SOURCE_DIR}/valhalla/odin/directionsbuilder.h
    ${valhalla_SOURCE_DIR}/valhalla/odin/enhancedtrippath.h
    ${valhalla_SOURCE_DIR}/valhalla/odin/maneuver.h
    ${valhalla_SOURCE_DIR}/valhalla/odin/maneuversbuilder.h
    ${valhalla_SOURCE_DIR}/valhalla/odin/narrativebuilder.h
    ${valhalla_SOURCE_DIR}/valhalla/odin/narrative_builder_factory.h
    ${valhalla_SOURCE_DIR}/valhalla/odin/narrative_dictionary.h
    ${valhalla_SOURCE_DIR}/valhalla/odin/sign.h
    ${valhalla_SOURCE_DIR}/valhalla/odin/signs.h
    ${valhalla_SOURCE_DIR}/valhalla/odin/transitrouteinfo.h
    ${valhalla_SOURCE_DIR}/valhalla/odin/util.h
    ${valhalla_SOURCE_DIR}/valhalla/odin/worker.h)

set(sources
    directionsbuilder.cc
    maneuversbuilder.cc
    narrative_dictionary.cc
    narrative_builder_factory.cc
    narrativebuilder.cc
    enhancedtrippath.cc
    maneuver.cc
    sign.cc
    signs.cc
    util.cc
    transitrouteinfo.cc
    worker.cc)

valhalla_module(NAME odin
  SOURCES ${sources}
  HEADERS ${headers}
  DEPENDS
    valhalla::proto
    date
    rapidjson
    Boost::boost
    ${MSVC_DEPENDS}
    ${valhalla_protobuf_targets})
