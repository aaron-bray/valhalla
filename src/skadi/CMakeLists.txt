
valhalla_module(NAME skadi
  SOURCES
    sample.cc
    util.cc
  HEADERS
    ${valhalla_SOURCE_DIR}/valhalla/skadi/sample.h
    ${valhalla_SOURCE_DIR}/valhalla/skadi/util.h
  DEPENDS
    valhalla::baldr
    Boost::boost
    ZLIB::ZLIB
    ${MSVC_DEPENDS})
