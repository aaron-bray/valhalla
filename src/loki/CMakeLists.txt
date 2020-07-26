set(headers
    ${valhalla_SOURCE_DIR}/valhalla/loki/node_search.h
    ${valhalla_SOURCE_DIR}/valhalla/loki/reach.h
    ${valhalla_SOURCE_DIR}/valhalla/loki/search.h
    ${valhalla_SOURCE_DIR}/valhalla/loki/worker.h)

set(sources
  search.cc
  worker.cc
  height_action.cc
  locate_action.cc
  reach.cc
  route_action.cc
  matrix_action.cc
  isochrone_action.cc
  trace_route_action.cc
  transit_available_action.cc
  node_search.cc)

valhalla_module(NAME loki
  SOURCES ${sources}
  HEADERS ${headers}
  DEPENDS
    valhalla::skadi
    valhalla::sif
    valhalla::proto
    Boost::boost
    date
    rapidjson
    ${MSVC_DEPENDS})
