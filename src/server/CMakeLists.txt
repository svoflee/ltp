include_directories (./
    ${SOURCE_DIR}/__util
    ${SOURCE_DIR}/__xml4nlp
    ${SOURCE_DIR}/__ltp_dll
    ${SOURCE_DIR}/_split_sentence
    ${SOURCE_DIR}/segmentor
    ${SOURCE_DIR}/postagger
    ${SOURCE_DIR}/ner
    ${SOURCE_DIR}/parser
    ${SOURCE_DIR}/srl
    ${SOURCE_DIR}/utils
    ${THIRDPARTY_DIR}/crfpp
    ${THIRDPARTY_DIR}/maxent
    ${THIRDPARTY_DIR}/tinyxml)

set (ltp_server_SRC           ltp_server.cpp mongoose.c mongoose.h)

link_directories ( ${LIBRARY_OUTPUT_PATH} )

add_executable (ltp_server     ${ltp_server_SRC})

target_link_libraries (ltp_server
    maxent_static_lib
    util_static_lib
    ltp
    splitsnt
    segmentor_static_lib
    postagger_static_lib
    parser_static_lib
    ner_static_lib
    srl_static_lib
    xml4nlp
    dl
    pthread
    boost_regex_static_lib)

