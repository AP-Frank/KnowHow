 How to use ipenvswitch
 ======================
 
 Bridging
 --------
	apt install openvswitch-switch
	ovs-vsctl add-br bridge

	ovs-vsctl add-port bridge enp2s0f0
	ovs-vsctl add-port bridge enp2s0f1
	ovs-vsctl show
	ovs-ofctl del-flows bridge
	ovs-ofctl add-flow bridge in_port=1,actions=output:2

	ip a

	ip link set dev enp2s0f0 up
	ip link set dev enp2s0f1 up

	ip link set dev bridge up
