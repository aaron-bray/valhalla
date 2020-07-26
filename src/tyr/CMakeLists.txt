set(headers
    ${valhalla_SOURCE_DIR}/valhalla/tyr/actor.h
    ${valhalla_SOURCE_DIR}/valhalla/tyr/serializers.h)

valhalla_module(NAME tyr
  SOURCES
    serializers.cc
    isochrone_serializer.cc
    matrix_serializer.cc
    height_serializer.cc
    locate_serializer.cc
    route_serializer.cc
    route_serializer_valhalla.cc
    route_serializer_osrm.cc
    transit_available_serializer.cc
    trace_serializer.cc
    actor.cc
  HEADERS
    ${headers}
  DEPENDS
    valhalla::loki
    valhalla::thor
    valhalla::odin
    valhalla::proto
    Boost::boost
    ${valhalla_protobuf_targets})
