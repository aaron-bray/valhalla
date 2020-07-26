set(headers
    ${valhalla_SOURCE_DIR}/valhalla/thor/astar.h
    ${valhalla_SOURCE_DIR}/valhalla/thor/astarheuristic.h
    ${valhalla_SOURCE_DIR}/valhalla/thor/attributes_controller.h
    ${valhalla_SOURCE_DIR}/valhalla/thor/bidirectional_astar.h
    ${valhalla_SOURCE_DIR}/valhalla/thor/costmatrix.h
    ${valhalla_SOURCE_DIR}/valhalla/thor/dijkstras.h
    ${valhalla_SOURCE_DIR}/valhalla/thor/edgestatus.h
    ${valhalla_SOURCE_DIR}/valhalla/thor/isochrone.h
    ${valhalla_SOURCE_DIR}/valhalla/thor/map_matcher.h
    ${valhalla_SOURCE_DIR}/valhalla/thor/multimodal.h
    ${valhalla_SOURCE_DIR}/valhalla/thor/optimizer.h
    ${valhalla_SOURCE_DIR}/valhalla/thor/pathalgorithm.h
    ${valhalla_SOURCE_DIR}/valhalla/thor/pathinfo.h
    ${valhalla_SOURCE_DIR}/valhalla/thor/route_matcher.h
    ${valhalla_SOURCE_DIR}/valhalla/thor/timedep.h
    ${valhalla_SOURCE_DIR}/valhalla/thor/timedistancematrix.h
    ${valhalla_SOURCE_DIR}/valhalla/thor/trafficalgorithm.h
    ${valhalla_SOURCE_DIR}/valhalla/thor/triplegbuilder.h
    ${valhalla_SOURCE_DIR}/valhalla/thor/worker.h)

set(sources
  astar.cc
  attributes_controller.cc
  bidirectional_astar.cc
  costmatrix.cc
  dijkstras.cc
  isochrone_action.cc
  isochrone.cc
  map_matcher.cc
  matrix_action.cc
  multimodal.cc
  optimized_route_action.cc
  optimizer.cc
  route_action.cc
  route_matcher.cc
  timedep_forward.cc
  timedep_reverse.cc
  timedistancematrix.cc
  trace_attributes_action.cc
  trace_route_action.cc
  triplegbuilder.cc
  worker.cc)

valhalla_module(NAME thor
  SOURCES ${sources}
  HEADERS ${headers}
  DEPENDS
    valhalla::proto
    valhalla::sif
    valhalla::meili
    date
    rapidjson
    robin_hood
    Boost::boost
  #VERBOSE
)
