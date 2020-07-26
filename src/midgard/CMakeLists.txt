set(headers
    ${valhalla_SOURCE_DIR}/valhalla/midgard/aabb2.h
    ${valhalla_SOURCE_DIR}/valhalla/midgard/constants.h
    ${valhalla_SOURCE_DIR}/valhalla/midgard/distanceapproximator.h
    ${valhalla_SOURCE_DIR}/valhalla/midgard/ellipse.h
    ${valhalla_SOURCE_DIR}/valhalla/midgard/encoded.h
    ${valhalla_SOURCE_DIR}/valhalla/midgard/gridded_data.h
    ${valhalla_SOURCE_DIR}/valhalla/midgard/linesegment2.h
    ${valhalla_SOURCE_DIR}/valhalla/midgard/logging.h
    ${valhalla_SOURCE_DIR}/valhalla/midgard/obb2.h
    ${valhalla_SOURCE_DIR}/valhalla/midgard/point2.h
    ${valhalla_SOURCE_DIR}/valhalla/midgard/pointll.h
    ${valhalla_SOURCE_DIR}/valhalla/midgard/polyline2.h
    ${valhalla_SOURCE_DIR}/valhalla/midgard/sequence.h
    ${valhalla_SOURCE_DIR}/valhalla/midgard/shape_decoder.h
    ${valhalla_SOURCE_DIR}/valhalla/midgard/tiles.h
    ${valhalla_SOURCE_DIR}/valhalla/midgard/util.h
    ${valhalla_SOURCE_DIR}/valhalla/midgard/util_core.h
    ${valhalla_SOURCE_DIR}/valhalla/midgard/vector2.h)

set(sources
  linesegment2.cc
  tiles.cc
  gridded_data.cc
  polyline2.cc
  obb2.cc
  pointll.cc
  aabb2.cc
  point2.cc
  util.cc
  ellipse.cc
  logging.cc
)

valhalla_module(NAME midgard
  SOURCES ${sources}
  HEADERS ${headers}
  DEPENDS
    Boost::boost
    ${MSVC_DEPENDS}
  #VERBOSE
)
