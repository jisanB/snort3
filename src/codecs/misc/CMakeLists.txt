
if(STATIC_CODECS)
    set(PLUGIN_LIST
        cd_gtp.cc
        cd_icmp4_ip.cc
        cd_icmp6_ip.cc
        cd_llc.cc
        cd_teredo.cc
        cd_user.cc
    )

else(STATIC_CODECS)
    add_shared_library(cd_gtp codecs cd_gtp.cc)
    add_shared_library(cd_icmp4_ip codecs cd_icmp4_ip.cc)
    add_shared_library(cd_icmp6_ip codecs cd_icmp6_ip.cc)
    add_shared_library(cd_llc codecs cd_llc.cc)
    add_shared_library(cd_teredo codecs cd_teredo.cc)
    add_shared_library(cd_user codecs cd_user.cc)

endif(STATIC_CODECS)

add_library( misc_codecs STATIC
    cd_default.cc
    ${PLUGIN_LIST}
)

target_link_libraries( misc_codecs
    protocols
    codec_module
)
