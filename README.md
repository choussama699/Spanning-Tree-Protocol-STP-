# Spanning-Tree-Protocol-STP-


tHIS lab shows how Spanning Tree Protocol prevents switching loops. Three switches are connected in a triangle. With STP running at its default settings, the switches elect a root bridge, assign port roles, and put one port into a blocking state to break the loop.

Topology
Device	Connected To
PC0	    Sw1
PC1	    Sw2
Sw1	    PC0, Sw2, Sw3
Sw2	    PC1, Sw1, Sw3
Sw3	    Sw1, Sw2


STP Result
Switch	Role / Port State
Sw3	Root Bridge (all ports designated)
Sw1	Root port toward Sw3; designated port toward Sw2
Sw2	Root port toward Sw3; blocking port toward Sw1

The redundant link between Sw1 and Sw2 is blocked on the Sw2 side. It stays as a backup path and becomes active if another link fails.

Objectives

Observe the root bridge election.
Identify root, designated and blocking ports.
Verify STP behavior 

Configuration

This lab uses the default STP configuration. Cisco switches run PVST+ by default, so no manual setup is needed. Just connect the switches with the cables shown in the topology.

Verification

Run on each switch:

show spanning-tree
show spanning-tree summary

Check the following:

Sw3 shows This bridge is the root.
Sw1 and Sw2 each show one Root port.
One port on Sw2 shows the BLK (blocking) state.
Optional: Set the Root Bridge Manually

By default, the root bridge is chosen by the lowest Bridge ID (priority + MAC address). To control the choice, set the priority on the desired switch:

spanning-tree vlan 1 priority 4096
