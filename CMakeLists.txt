set(CMAKE_MODULE_PATH 
    ${CMAKE_MODULE_PATH}
    "${CMAKE_CURRENT_SOURCE_DIR}/cmake/"
    )

find_package(Protobuf REQUIRED)

set(PROTO_DEFS
    def/wrapper.proto
    def/misc.proto
    def/vars.proto
    def/funcs.proto
    def/classes.proto
    def/tmpl.proto
	def/base.proto
    )

include_directories(${PROTOBUF_INCLUDE_DIRS})
protobuf_generate_cpp(PROTO_SRCS PROTO_HDRS ${PROTO_DEFS})

set(CPPTOOL_PROTO_INCLUDES ${PROTOBUF_INCLUDE_DIRS} ${CMAKE_CURRENT_BINARY_DIR} PARENT_SCOPE)
set(CPPTOOL_PROTO_LIBRARY cppToolProto PARENT_SCOPE)

add_definitions(-DGOOGLE_PROTOBUF_NO_RTTI -D_SCL_SECURE_NO_WARNINGS)

add_library(cppToolProto STATIC ${PROTO_SRCS} ${PROTO_HDRS})
target_link_libraries(cppToolProto ${PROTOBUF_LIBRARIES})

# Custom targets for java and python bindings
include(ProtobufExtend)
generate_extra_protobuf_language(Java --java_out ${PROTO_DEFS})
generate_extra_protobuf_language(Python --python_out ${PROTO_DEFS})
