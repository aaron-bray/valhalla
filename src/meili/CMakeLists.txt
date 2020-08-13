set(headers
    ${valhalla_SOURCE_DIR}/valhalla/meili/candidate_search.h
    ${valhalla_SOURCE_DIR}/valhalla/meili/emission_cost_model.h
    ${valhalla_SOURCE_DIR}/valhalla/meili/geometry_helpers.h
    ${valhalla_SOURCE_DIR}/valhalla/meili/grid_range_query.h
    ${valhalla_SOURCE_DIR}/valhalla/meili/grid_traversal.h
    ${valhalla_SOURCE_DIR}/valhalla/meili/map_matcher.h
    ${valhalla_SOURCE_DIR}/valhalla/meili/map_matcher_factory.h
    ${valhalla_SOURCE_DIR}/valhalla/meili/match_result.h
    ${valhalla_SOURCE_DIR}/valhalla/meili/measurement.h
    ${valhalla_SOURCE_DIR}/valhalla/meili/priority_queue.h
    ${valhalla_SOURCE_DIR}/valhalla/meili/routing.h
    ${valhalla_SOURCE_DIR}/valhalla/meili/state.h
    ${valhalla_SOURCE_DIR}/valhalla/meili/stateid.h
    ${valhalla_SOURCE_DIR}/valhalla/meili/topk_search.h
    ${valhalla_SOURCE_DIR}/valhalla/meili/traffic_segment_matcher.h
    ${valhalla_SOURCE_DIR}/valhalla/meili/transition_cost_model.h
    ${valhalla_SOURCE_DIR}/valhalla/meili/viterbi_search.h)

set(sources
  viterbi_search.cc
  topk_search.cc
  routing.cc
  candidate_search.cc
  transition_cost_model.cc
  map_matcher.cc
  map_matcher_factory.cc
  match_route.cc)

valhalla_module(NAME meili
  SOURCES ${sources}
  HEADERS ${headers}
  DEPENDS
    valhalla::sif
    date
    rapidjson
    Boost::boost
    ${MSVC_DEPENDS}
    ${valhalla_protobuf_targets}
)
