set(LIB "hashing")

find_package(Boost COMPONENTS thread system program_options date_time filesystem REQUIRED)

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -std=c11 -D_GNU_SOURCE")

include_directories(${Boost_INCLUDE_DIRS})
include_directories("${MONERO_DIR}/contrib/epee/include")
include_directories("${MONERO_DIR}/src")

link_directories(${MONERO_DIR}/src/crypto)

add_library(${LIB} SHARED src/hashing.c)

target_link_libraries(${LIB} cncrypto)
