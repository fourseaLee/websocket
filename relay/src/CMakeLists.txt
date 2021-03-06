cmake_minimum_required(VERSION 2.8)

project(relay_server)

include_directories(./)


set(compat_src  compat/glibc_compat.cpp
                compat/glibc_sanity.cpp
                compat/glibcxx_sanity.cpp
                compat/strnlen.cpp)

set(crypto_src  #crypto/aes.cpp
                crypto/chacha20.cpp
                crypto/hmac_sha256.cpp
                crypto/hmac_sha512.cpp
                crypto/poly1305.c
                crypto/ripemd160.cpp
                crypto/sha1.cpp
                crypto/sha256.cpp
                crypto/sha256_sse4.cpp
                crypto/sha512.cpp
                #crypto/ctaes/ctaes.c
                )

set(rpc_src rpc/protocol.cpp
            rpc/server.cpp
			rpc/client.cpp
            rpc/relay.cpp)

set(support_src support/cleanse.cpp
                support/lockedpool.cpp)

set(base_src    
                base58.cpp
                bech32.cpp
                fs.cpp
                hash.cpp
                httprpc.cpp
                httpserver.cpp
                netaddress.cpp
                netbase.cpp           
                random.cpp
                rest.cpp
                sync.cpp
                scheduler.cpp
                threadinterrupt.cpp
                uint256.cpp
                util.cpp
                utilstrencodings.cpp
                utiltime.cpp
                warnings.cpp
                timedata.cpp
                )

find_package(OpenSSL)
set(basic_link_lib c rt pthread event event_pthreads boost_system boost_chrono boost_program_options boost_filesystem boost_thread ssl crypto)

set(relayd_src    ${compat_src}
                    ${crypto_src}
                    ${rpc_src}
                    ${support_src}
                    ${base_src}
                    main.cpp)

add_executable(relayd ${relayd_src})

target_link_libraries(relayd ${basic_link_lib})

