set(headers ${valhalla_SOURCE_DIR}/valhalla/sif/autocost.h
            ${valhalla_SOURCE_DIR}/valhalla/sif/bicyclecost.h
            ${valhalla_SOURCE_DIR}/valhalla/sif/costconstants.h
            ${valhalla_SOURCE_DIR}/valhalla/sif/costfactory.h
            ${valhalla_SOURCE_DIR}/valhalla/sif/dynamiccost.h
            ${valhalla_SOURCE_DIR}/valhalla/sif/edgelabel.h
            ${valhalla_SOURCE_DIR}/valhalla/sif/hierarchylimits.h
            ${valhalla_SOURCE_DIR}/valhalla/sif/motorcyclecost.h
            ${valhalla_SOURCE_DIR}/valhalla/sif/motorscootercost.h
            ${valhalla_SOURCE_DIR}/valhalla/sif/nocost.h
            ${valhalla_SOURCE_DIR}/valhalla/sif/pedestriancost.h
            ${valhalla_SOURCE_DIR}/valhalla/sif/transitcost.h
            ${valhalla_SOURCE_DIR}/valhalla/sif/truckcost.h)

set(sources
  autocost.cc
  bicyclecost.cc
  hierarchylimits.cc
  motorcyclecost.cc
  motorscootercost.cc
  nocost.cc
  pedestriancost.cc
  transitcost.cc
  truckcost.cc
  dynamiccost.cc)

valhalla_module(NAME sif
  SOURCES ${sources}
  HEADERS ${headers}
  DEPENDS
    valhalla::baldr
    valhalla::proto
    date
    rapidjson
    Boost::boost
    ${MSVC_DEPENDS}
    ${valhalla_protobuf_targets}
)
