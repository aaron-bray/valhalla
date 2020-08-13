## Process the IANA Time Zone Database files
set(tz_db_files africa antarctica asia australasia backward etcetera europe
  pacificnew northamerica southamerica systemv leapseconds)

foreach(tz_db_file ${tz_db_files})
  add_custom_command(OUTPUT ${CMAKE_CURRENT_BINARY_DIR}/date_time_${tz_db_file}.h
    COMMAND ${CMAKE_COMMAND} -DMSVC=${MSVC} -P ${valhalla_SOURCE_DIR}/cmake/Binary2Header.cmake
        ${valhalla_SOURCE_DIR}/date_time/${tz_db_file}
        ${CMAKE_CURRENT_BINARY_DIR}/date_time_${tz_db_file}.h
        --variable-name date_time_${tz_db_file} --skip 1 --raw
    WORKING_DIRECTORY ${valhalla_SOURCE_DIR}
    COMMENT "Compiling date_time/${tz_db_file} to date_time_${tz_db_file}.h"
    DEPENDS ${valhalla_SOURCE_DIR}/date_time/${tz_db_file})
endforeach()

## Process the windowsZones.xml file
add_custom_command(OUTPUT ${CMAKE_CURRENT_BINARY_DIR}/date_time_windows_zones.h
  COMMAND ${CMAKE_COMMAND} -DMSVC=${MSVC} -P ${valhalla_SOURCE_DIR}/cmake/Binary2Header.cmake
      ${valhalla_SOURCE_DIR}/date_time/windowsZones.xml
      ${CMAKE_CURRENT_BINARY_DIR}/date_time_windows_zones.h
      --variable-name date_time_windows_zones_xml --skip 1 --raw
  WORKING_DIRECTORY ${valhalla_SOURCE_DIR}
  COMMENT "Compiling date_time/windowsZones.xml to date_time_windows_zones.h"
  DEPENDS ${valhalla_SOURCE_DIR}/date_time/windowsZones.xml)

set(headers
    ${valhalla_SOURCE_DIR}/valhalla/baldr/accessrestriction.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/admin.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/admininfo.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/complexrestriction.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/compression_utils.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/connectivity_map.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/curler.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/curl_tilegetter.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/datetime.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/directededge.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/double_bucket_queue.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/edgeinfo.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/edgetracker.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/graphconstants.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/graphid.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/graphreader.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/graphtile.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/graphtileheader.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/json.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/laneconnectivity.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/location.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/merge.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/nodeinfo.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/nodetransition.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/openlr.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/pathlocation.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/predictedspeeds.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/rapidjson_utils.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/sign.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/signinfo.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/streetname.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/streetnames.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/streetnames_factory.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/streetnames_us.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/streetname_us.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/tilegetter.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/tilehierarchy.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/timedomain.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/time_info.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/traffictile.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/transitdeparture.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/transitroute.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/transitschedule.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/transitstop.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/transittransfer.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/turn.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/turnlanes.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/verbal_text_formatter.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/verbal_text_formatter_factory.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/verbal_text_formatter_us.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/verbal_text_formatter_us_co.h
    ${valhalla_SOURCE_DIR}/valhalla/baldr/verbal_text_formatter_us_tx.h)

set(sources
    accessrestriction.cc
    admin.cc
    compression_utils.cc
    connectivity_map.cc
    curler.cc
    datetime.cc
    directededge.cc
    edgeinfo.cc
    graphid.cc
    graphreader.cc
    graphtile.cc
    graphtileheader.cc
    edgetracker.cc
    merge.cc
    nodeinfo.cc
    openlr.cc
    location.cc
    pathlocation.cc
    tilehierarchy.cc
    turn.cc
    streetname.cc
    streetnames.cc
    streetnames_factory.cc
    streetname_us.cc
    streetnames_us.cc
    transitdeparture.cc
    transitroute.cc
    transitschedule.cc
    transittransfer.cc
    laneconnectivity.cc
    verbal_text_formatter.cc
    verbal_text_formatter_us.cc
    verbal_text_formatter_us_co.cc
    verbal_text_formatter_us_tx.cc
    verbal_text_formatter_factory.cc)

#basic timezone stuff
list(APPEND headers
    ${CMAKE_CURRENT_BINARY_DIR}/date_time_africa.h
    ${CMAKE_CURRENT_BINARY_DIR}/date_time_antarctica.h
    ${CMAKE_CURRENT_BINARY_DIR}/date_time_asia.h
    ${CMAKE_CURRENT_BINARY_DIR}/date_time_australasia.h
    ${CMAKE_CURRENT_BINARY_DIR}/date_time_backward.h
    ${CMAKE_CURRENT_BINARY_DIR}/date_time_etcetera.h
    ${CMAKE_CURRENT_BINARY_DIR}/date_time_europe.h
    ${CMAKE_CURRENT_BINARY_DIR}/date_time_leapseconds.h
    ${CMAKE_CURRENT_BINARY_DIR}/date_time_northamerica.h
    ${CMAKE_CURRENT_BINARY_DIR}/date_time_pacificnew.h
    ${CMAKE_CURRENT_BINARY_DIR}/date_time_southamerica.h
    ${CMAKE_CURRENT_BINARY_DIR}/date_time_systemv.h
    ${CMAKE_CURRENT_BINARY_DIR}/date_time_windows_zones.h)
list(APPEND sources tz_alt.cpp)

#ios we have more work to make use of system tzdb
if(APPLE)
  list(APPEND sources ${valhalla_SOURCE_DIR}/third_party/date/src/ios.mm)
endif()

valhalla_module(NAME baldr
  SOURCES
    ${sources}
  HEADERS
    ${headers}
  DEPENDS
    valhalla::midgard
    valhalla::proto
    date
    rapidjson
    Boost::boost
    ZLIB::ZLIB
    ${MSVC_DEPENDS}
    ${valhalla_protobuf_targets}
  #VERBOSE
)
