# DPDK-HYPERSCAN-SAMPLE

Purpose: combining hyperscan pattern matching with DPDK allows use of DPI with packet parse-processing functionlities. This especially useful in case of VM or Network functions

pre-requisties:-
DPDK - build for target machine
HYPERSCAN - build for target machine

note: both dpdk and hyperscan should be build with archive mode.

build:-

enviroment variables:-
 HYPERSCAN_SDK - path to hyperscan build path
 RTE_SDK - dpdk sdk path
 RTE_TARGET - dpdk build target path
 
g++ -O3 -o test node.c main.c -I${HYPERSCAN_SDK}/include/ -I${RTE_SDK}${RTE_TARGET}/include ${HYPERSCAN_SDK}/lib/libhs.a -Wl,--whole-archive -L${RTE_SDK}${RTE_TARGET}/lib/ -L${RTE_SDK}${RTE_TARGET}/lib/libintel_dpdk.a -lrt -ldl -lpthread -Wl,--no-whole-archive
